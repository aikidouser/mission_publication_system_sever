# Mission Publication System - Sever Side

- [ ] Socket
  - [ ] handle msg
- [ ] Sign in
  - [x] Check the account and password correct
- [ ] Sign up 
  - [x] Set the user name
  - [x] Check if there are the same account
- [ ] Mission

# Account manage

## init 

```python
user = AccountManage(account, password)
```

## Sign up

```python
if_suc_signup = user.signup(username)
```

- 將回傳是否成功註冊
  - False
    - 已存在相同的帳號
  - True
    - 無相同帳號
    - 寫入json檔儲存

## Sign in

```python
if_suc_signin = user.signin()
```

- 回傳是否成功登入

  - False

    - 帳號 or 密碼有錯

    - 要求重新輸入

      > 重新建立新物件

  - True

    - 可繼續執行

# msg

## Account
- information
    - account
    - password
    - user name

- sign in
    ```python=
    account signin 'account' 'password'
    ```

- sign up
    ```python=
    account regist 'account' 'password' 'username'
    ```

## Mission

- information
    - name
    - destination
    - deadline
    - salary
    - content

- create
    - client -> sever
        ```python=
        mission create 'missionname' 'destination' 'deadline' 'salary' 'content'
        ```

- read
    - client -> sever
        ```python=
        mission read
        ```
    - sever -> client
        ```python=
        mission read 'missionname' 'missionname' ......
        ```

- detail
    - client -> sever
        ```python=
        mission detail 'missionname'
        ```
    - sever -> client
        ```python=
        mission detail 'missionname' 'destination' 'deadline' 'salary' 'content'
        ```

- get
    ```python=
    mission get 'missionname'
    ```
    > 比對 跟任務不同的 account 才可以 get

- complete
    ```python=
    mission complete 'missionname'
    ```
    > 比對 跟任務相同的 account 才可以 complete

## def msg handler

- return: 
    - dict
    - like the information above

- arg: 
    - str(msg, encodeing='Big5')

    ```python=
    msg_dict = msg_handler(str(msg))
    ```