<template>
  <div class="body">
    <div class="center">
      <h1>Login</h1>
      <form action="">
        <div class="txt_field">
          <input type="text">
          <span></span>
          <label for="">Username</label>
        </div>
        <div class="txt_field">
          <input type="password">
          <span></span>
          <label for="">Password</label>
        </div>
        <div class="pass">Forgot Password?</div>
        <input type="submit" value="Login">
        <div class="signup_link">Not a member?
          <a href="#">Signup</a>
        </div>
      </form>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.body {
  margin: 0;
  padding: 0;
  font-family: montserrat;
  background: linear-gradient(120deg, #2980b9, #8e44ad);
  height: 100vh;
  overflow: hidden;
}

.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 400px;
  background: #fff;
  border-radius: 10px;

  h1 {
    text-align: center;
    padding: 0 0 20px 0;
    border-bottom: 1px solid silver;
  }

  form {
    padding: 0 40px;
    box-sizing: border-box;

    .txt_field {
      position: relative;
      border-bottom: 2px solid #adadad;
      margin: 30px 0;

      input {
        width: 100%;
        padding: 0 5px;
        height: 40px;
        font-style: 16px;
        border: none;
        bottom: none;
        outline: none;

        &:focus {
          &~label {
            top: -5px;
            color: #2691d9;
          }

          &~span::before {
            width: 100%;
          }
        }
      }

      label {
        position: absolute;
        top: 50%;
        left: 5px;
        color: #adadad;
        transform: translateY(-50%);
        font-size: 16px;
        pointer-events: none;
        transition: .5s;
      }

      span::before {
        content: '';
        position: absolute;
        top: 40px;
        left: 0;
        width: 0;
        height: 2px;
        background: #2691d9;
        transition: .5s;
      }
    }

    .pass {
      margin: -5px 0 20px 5px;
      color: #a6a6a6;
      cursor: pointer;

      &:hover {
        text-decoration: underline;
      }
    }

    input[type="submit"] {
      width: 100%;
      height: 50px;
      border: 1px solid;
      background: #2691d4;
      border-radius: 25px;
      font-size: 18px;
      color: #e9f4fb;
      font-weight: 700;
      cursor: pointer;
      outline: none;

      &:hover {
        border-color: #2691d4;
        transition: .5s;
      }
    }

    .signup_link {
      margin: 30px 0;
      text-align: center;
      font-size: 16px;
      color: #666;

      a {
        color: #2691d9;
        text-decoration: none;

        &:hover {
          text-decoration: underline;
        }
      }
    }
  }
}
</style>