<template>
  <section id="contact" class="contact">
    <h2>How to reach us</h2>
    <p class="description">Lorem ipsum dolor sit amet, consectetur.</p>

    <div class="form-container">
      <!-- Form -->
      <div class="form-box">
        <form @submit.prevent="handleSubmit" novalidate>
          <div class="form-row">
            <div class="form-group">
              <label>First Name *</label>
              <input
                type="text"
                v-model="form.firstName"
                :class="{ error: errors.firstName }"
                placeholder="First Name"
              />
              <p v-if="errors.firstName" class="error-msg">
                First name is required
              </p>
            </div>

            <div class="form-group">
              <label>Last Name *</label>
              <input
                type="text"
                v-model="form.lastName"
                :class="{ error: errors.lastName }"
                placeholder="Last Name"
              />
              <p v-if="errors.lastName" class="error-msg">
                Last name is required
              </p>
            </div>
          </div>

          <div class="form-group">
            <label>Email *</label>
            <input
              type="email"
              v-model="form.email"
              :class="{ error: errors.email }"
              placeholder="Email"
            />
            <p v-if="errors.email" class="error-msg">
              Valid email is required
            </p>
          </div>

          <div class="form-group">
            <label>Telephone</label>
            <input
              type="tel"
              v-model="form.telephone"
              placeholder="Telephone"
            />
          </div>

          <div class="form-group">
            <label>Message</label>
            <textarea
              v-model="form.message"
              :class="{ error: errors.message }"
              rows="3"
              placeholder="Message"
            ></textarea>
            <p v-if="errors.message" class="error-msg">
              Message is required
            </p>
          </div>

          <p class="small-text">* required fields</p>

          <div class="form-group terms">
            <input type="checkbox" v-model="form.agree" id="agree" />
            <label for="agree">
              I agree to the
              <a href="#" class="link">Terms & Conditions</a>
            </label>
          </div>

          <button type="submit">SUBMIT</button>
        </form>
      </div>

      <!-- Map -->
      <div class="form-box map-box">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d7921.714234862977!2d79.88948013955658!3d6.907683372366787!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3ae259f32de39911%3A0x28e9030fbb5df9ab!2sRajagiriya%2C%20Sri%20Jayawardenepura%20Kotte!5e0!3m2!1sen!2slk!4v1751481080717!5m2!1sen!2slk"    
          width="200%"
          height="600"
          style="border:0;"
          allowfullscreen=""
          loading="lazy"
        ></iframe>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      form: {
        firstName: '',
        lastName: '',
        email: '',
        telephone: '',
        message: '',
        agree: false
      },
      errors: {}
    };
  },
  methods: {
    validateForm() {
      this.errors = {};
      if (!this.form.firstName.trim()) this.errors.firstName = true;
      if (!this.form.lastName.trim()) this.errors.lastName = true;
      if (
        !this.form.email.match(
          /^[^\s@]+@[^\s@]+\.[^\s@]+$/
        )
      ) {
        this.errors.email = true;
      }
      if (!this.form.message.trim()) this.errors.message = true;
      if (!this.form.agree) {
        alert('You must agree to the Terms & Conditions.');
        return false;
      }
      return Object.keys(this.errors).length === 0;
    },
    handleSubmit() {
      if (this.validateForm()) {
        alert(
          `Form submitted!\n\n${JSON.stringify(
            this.form,
            null,
            2
          )}`
        );
        // Reset the form
        this.form = {
          firstName: '',
          lastName: '',
          email: '',
          telephone: '',
          message: '',
          agree: false
        };
      }
    }
  }
};
</script>

<style scoped>
.contact {
  padding: 40px 0;
  color: #fff;
  background: #000;
  width: 100%;
}

.description {
  color: #aaa;
  margin-bottom: 40px;
  max-width: 1400px;
  margin-left: 10%;
  margin-right: 10%;
  padding: 0;
}

.contact h2 {
  margin: 0 10% 20px 10%;
  padding: 0;
}

.form-container {
  display: flex;
  flex-wrap: wrap;
  gap: 40px;
  max-width: none;
  margin: 0 10%;
  padding: 0;
}

.form-box {
  flex: 1 1 400px;
  max-width: 750px;
}

.form-row {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
}

.form-group {
  margin-bottom: 25px;
  flex: 1;
  min-width: 180px;
}

label {
  display: block;
  margin-bottom: 8px;
  font-size: 14px;
  color: #fff;
}

input,
textarea {
  width: 100%;
  padding: 12px;
  background: #333;
  border: 1px solid #555;
  border-radius: 4px;
  color: #fff;
  font-size: 1rem;
  box-sizing: border-box;
}

input::placeholder,
textarea::placeholder {
  color: #888;
}

.error {
  border-color: red;
}

.error-msg {
  color: red;
  font-size: 0.9rem;
  margin-top: 5px;
}

.small-text {
  color: #aaa;
  font-size: 13px;
  margin-top: -10px;
  margin-bottom: 20px;
}

.terms {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  margin-bottom: 25px;
}

.terms input[type="checkbox"] {
  width: auto;
  margin-top: 2px;
}

.terms label {
  margin-bottom: 0;
  font-size: 13px;
  line-height: 1.4;
}

button {
  background: #d79e1e;
  color: #fff;
  padding: 12px 40px;
  font-size: 1rem;
  font-weight: bold;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  width: 30%;
  margin-top: 10px;
  float: right;
}

button:hover {
  background: #c68900;
}

.map-box iframe {
  width: 120%;
  height: 500px;
  border-radius: 8px;
  border: none;
}

@media (max-width: 1024px) {
  .form-container {
    margin: 0 8%;
    gap: 30px;
  }
  
  .contact h2 {
    margin: 0 8% 20px 8%;
  }
  
  .description {
    margin-left: 8%;
    margin-right: 8%;
  }
  
  .map-box iframe {
    width: 100%;
    height: 450px;
  }
}

@media (max-width: 768px) {
  .form-container {
    flex-direction: column;
    margin: 0 5%;
    gap: 25px;
  }
  
  .contact h2 {
    margin: 0 5% 20px 5%;
    font-size: 1.8rem;
  }
  
  .description {
    margin-left: 5%;
    margin-right: 5%;
  }
  
  .form-box {
    max-width: 100%;
  }
  
  .form-row {
    flex-direction: column;
    gap: 0;
  }
  
  .form-group {
    min-width: 100%;
  }
  
  button {
    width: 100%;
    float: none;
  }
  
  .map-box iframe {
    width: 100%;
    height: 350px;
  }
}

@media (max-width: 480px) {
  .contact {
    padding: 30px 0;
  }
  
  .form-container {
    margin: 0 4%;
    gap: 20px;
  }
  
  .contact h2 {
    margin: 0 4% 15px 4%;
    font-size: 1.6rem;
  }
  
  .description {
    margin-left: 4%;
    margin-right: 4%;
    font-size: 0.9rem;
  }
  
  input,
  textarea {
    padding: 10px;
    font-size: 0.9rem;
  }
  
  label {
    font-size: 13px;
  }
  
  button {
    padding: 10px 30px;
    font-size: 0.9rem;
  }
  
  .map-box iframe {
    width: 100%;
    height: 300px;
    border-radius: 6px;
  }
  
  .terms label {
    font-size: 12px;
  }
  
  .small-text {
    font-size: 12px;
  }
}
</style>
