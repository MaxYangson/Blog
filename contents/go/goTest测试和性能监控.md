# Go Test测试

最近在写go项目的时候，经常遇到需要测试某个函数的情况，之前每次需要写一个main函数来测试，显然不够标准。因此研究一下go的测试工具goTest，计划以后用goTest来做单元测试。

## 快速学习

单元测试( unit test)，就是一种为验证单元的正确性而设置的自动化测试，一个单元就是程序中的一个模块化部分。一般来说，一个单元通常会与程序中的一个函数或者一个方法相对应，但这并不是必须的。

Go 的单元测试需要用到 testing 包 以及 go test 命令，而且对测试文件也有以下要求：

1) 被测试的源文件和测试文件必须位于同一个包下

2) 测试文件必须要以_test.go 结尾
   
   + 虽然 Go 对测试文件_test.go 的前缀没有强制要求，不过一般我们都设置为被测试的文件的文件名，如:要对 user.go 进行测试，那么测试文件的 名字我们通常设置为 user_test.go

3) 测试文件中的测试函数为 TestXxx(t *testing.T)
   
   + 其中 Xxx 的首字母必须是大写的英文字母
   
   + 函数参数必须是 testing.T 的指针类型(如果是 Benchmark 测试则参数是testing.B 的指针类型)

1 在 user_test.go 中测试添加员工的方法

```go
func TestAddUser(t *testing.T) {
    fmt.Println("测试添加用户：")
    user := &User{
        Username: "admin3",
        Password: "123456",
        Email:  "admin3@atguigu.com",
    }
    //将 user 添加到数据库中
    user.AddUser()
}
// 然后执行go test命令
```

2 如果一个测试函数的函数名的不是以 Test 开头，那么在使用 go test 命令时默认不会执行，不过我们可以设置该函数时一个子测试函数，可以在其他测试函数里通过 t.Run 方法来执行子测试函数，具体代码如下：

```go
func TestUser(t *testing.T) {
t.Run("正在测试添加用户：", testAddUser)
t.Run("正在测试获取一个用户：", testGetUserById)
}
//子测试函数
func testAddUser(t *testing.T) {
fmt.Println("测试添加用户：")
user := &User{
Username: "admin5",
Password: "123456",
Email: "admin5@atguigu.com",
}
//将 user 添加到数据库中
user.AddUser()
}
//子测试函数
func testGetUserByID(t *testing.T) {
u := &User{}
user, _ := u.GetUserByID(1)
fmt.Println("用户的信息是：", *user)
}
```

3 我们还可以通过 TestMain(m *testing.M)函数在测试之前和之后做一些其他的操作

a) 测试文件中有 TestMain 函数时，执行 go test 命令将直接运行 TestMain

函数，不直接运行测试函数，只有在 TestMain 函数中执行 m.Run()时才

会执行测试函数

b) 如果想查看测试的详细过程，可以使用 go test -v 命令

c) 具体代码

```go
func TestMain(m *testing.M) {
fmt.Println("开始测试")
m.Run()
}
func TestUser(t *testing.T) {
t.Run("正在测试添加用户：", testAddUser)
}
func testAddUser(t *testing.T) {
fmt.Println("测试添加用户：")
user := &User{
Username: "admin5",
Password: "123456",
Email: 
"admin5@atguigu.com",
}
//将 user 添加到数据库中
user.AddUser()
}
```

-----

<p style="text-align:right">Lastest Updated: {docsify-updated}</p>