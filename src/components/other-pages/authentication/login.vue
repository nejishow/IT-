<template>
  <div>
    <!-- Start Page Title -->
    <div class="page-title-area">
      <div class="d-table">
        <div class="d-table-cell">
          <div class="container">
            <h2>Connection</h2>
          </div>
        </div>
      </div>

      <div class="shape1">
        <img src="../../../assets/img/shape1.png" alt="shape" />
      </div>
      <div class="shape2 rotateme">
        <img src="../../../assets/img/shape2.svg" alt="shape" />
      </div>
      <div class="shape3">
        <img src="../../../assets/img/shape3.svg" alt="shape" />
      </div>
      <div class="shape4">
        <img src="../../../assets/img/shape4.svg" alt="shape" />
      </div>
      <div class="shape5">
        <img src="../../../assets/img/shape5.png" alt="shape" />
      </div>
      <div class="shape6 rotateme">
        <img src="../../../assets/img/shape4.svg" alt="shape" />
      </div>
      <div class="shape7">
        <img src="../../../assets/img/shape4.svg" alt="shape" />
      </div>
      <div class="shape8 rotateme">
        <img src="../../../assets/img/shape2.svg" alt="shape" />
      </div>
    </div>
    <section class="about-area ptb-80">
      <div class="container">
        <form class="form-horizontal auth-form" @submit.prevent="handleSubmit">
          <div class="form-group">
            <input v-model="email" name="login[username]" type="email" class="form-control" id="exampleInputEmail1" />
          </div>
          <div class="form-group">
            <input :type="type" v-model="password" name="login[password]" class="form-control" />
          </div>

          <div class="form-button">
            <button class="btn btn-primary" type="submit" @click="login">
              Se connecter
            </button>
          </div>
          <div class="form-terms">
            <div class="custom-control custom-checkbox mr-sm-2">
              <a href="#" class="mt-4">
                <router-link to="/register">Pas encore enregistrĂ©? Enregistrez vous!</router-link>
              </a>
            </div>
          </div>
        </form>
      </div>
    </section>
  </div>
</template>

<script>
import AuthService from "../../../services/auth";
export default {
  components: {},
  data() {
    return {
      type: "password",
      email: "",
      password: "",
      submitted: false,
    };
  },
  created() {
    // reset login status for JWT
    //  this.$store.dispatch("authentication/logout");
  },
  methods: {
    handleSubmit() {
      this.submitted = true;
    },
    async login() {
      this.submitted = true;
      if (this.email == "" && this.password == "") {
        this.$toasted.show(
          "Oops... veuillez entrez un identifiant et un mot de passe valide",
          {
            theme: "bubble",
            position: "bottom-right",
            type: "error",
            duration: 2000,
          }
        );
      } else {
        await AuthService.login(this.email, this.password)
          .then(async (authResult) => {
            await this.$store.dispatch("afterLogin", authResult.user.uid);


            this.$toasted.show("Connection Ă©tablit", {
              theme: "bubble",
              position: "top-right",
              type: "success",
              duration: 3000,
            });
            this.$router.push("/");
          })
          .catch((error) => {
            // eslint-disable-next-line no-console
            this.$toasted.show(error, {
              theme: "bubble",
              position: "top-right",
              type: "danger",
              duration: 2000,
            });
          });
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.container {
  max-width: 900px;

  .bg-primary {
    padding: 50px;
    background-image: url("../../../assets/img/logo.png");
    background-position: center;
    box-shadow: 1px 5px 24px 0 rgba(255, 128, 132, 0.8);
  }

  .form-group {
    margin-bottom: 1.5rem;
  }

  .svg-icon {
    padding: 24px;
    margin: 0 auto;
    border: 2px dashed #ffffff;
    border-radius: 100%;
    height: 130px;
    width: 130px;
    margin-bottom: 40px;

    svg {
      height: 80px;
    }
  }

  p {
    color: rgba(#ffffff, 0.9);
    font-size: 15px;
    line-height: 2;
    text-align: center;
  }

  h3 {
    color: #ffffff;
    font-weight: 600;
    text-align: center;
  }
}
</style>
