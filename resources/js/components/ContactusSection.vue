<template>
    <!-- ======= Contact us Section Start ======= -->
    <section id="contactus_section" class="sec">
        <div class="container">
            <div class="section-title text-center mb-30">
                <h2 class="title">Contact Us</h2>
            </div>
            <div class="row justify-content-center my-5 py-5">
                <div class="col-lg-5 mt-5 p-5 border-end d-flex algn-items-center justify-content-center flex-column">
                    <div class="form_heading mb-4">
                        <h3>Send us a message</h3>
                    </div>
                    <form @submit.prevent="submitForm" class="contact_form w-100">
                        <div class="d-flex gap-3">
                            <div class="form-floating w-100">
                                <input v-model="formData.name" type="text" name="name" class="form-control" id="name"
                                    placeholder="enter name">
                                <label for="name">Name</label>
                                <div class="error-message bg-danger badge" v-show="formErrorName">{{ formErrorName }}
                                </div>
                            </div>

                            <div class="form-floating w-100">
                                <input v-model="formData.email" type="email" class="form-control" name="email"
                                    id="email" placeholder="enter email">
                                <label for="email">Email</label>
                                <div class="error-message bg-danger badge" v-show="formErrorEmail">{{ formErrorEmail }}
                                </div>
                            </div>
                        </div>
                        <div class="form-floating mt-3">
                            <input v-model="formData.phone" type="text" class="form-control" name="phone" id="phone"
                                placeholder="enter phone no">
                            <label for="phone">Phone no</label>
                            <div class="error-message bg-danger badge" v-show="formErrorPhone">{{ formErrorPhone }}
                            </div>
                        </div>
                        <div class="form-floating mt-3">
                            <textarea v-model="formData.message" class="form-control" name="message" id="message"
                                rows="10" placeholder="enter message"></textarea>
                            <label for="message">Message</label>
                        </div>
                        <div class="my-3">
                            <div class="sent-message badge bg-success" v-show="formSuccess">Your message has been
                                sent. Thank you!</div>
                        </div>
                        <div class="linkWrap">
                            <button type="submit" class="style-25">
                                <span class="wrap">
                                    <div class="text" data-text="Send">Send Us</div>
                                </span>
                            </button>
                        </div>
                    </form>
                </div>
                <div class="col-lg-7">
                    <img src="https://img.freepik.com/free-vector/mail-sent-concept-illustration_114360-96.jpg?size=626&amp;ext=jpg&amp;ga=GA1.2.1741584830.1690997931&amp;semt=ais"
                        class="img-fluid" loading="lazy">
                </div>
            </div>
        </div>
    </section>
</template>
<script>
import { useToast } from 'vue-toast-notification';
import axios from 'axios';

export default {
    data() {
        return {
            formData: {
                name: '',
                email: '',
                phone: '',
                message: ''
            },
            formErrorName: '',
            formErrorEmail: '',
            formErrorPhone: '',
            formSuccess: false
        };
    },
    methods: {
        async submitForm() {
            try {
                // Validate form fields
                if (!this.formData.name) {
                    this.formErrorName = 'Name is required';
                    this.formSuccess = false;
                    return;
                }
                if (!this.formData.email) {
                    this.formErrorEmail = 'Email is required';
                    this.formSuccess = false;
                    return;
                }
                if (!this.formData.phone) {
                    this.formErrorPhone = 'Phone is required';
                    this.formSuccess = false;
                    return;
                }

                this.formErrorName = '';
                this.formErrorEmail = '';
                this.formErrorPhone = '';

                await axios.post('/submit-form', this.formData);

                const toast = useToast();
                toast.open({
                    message: 'Message Sent Successfully!!',
                    type: 'success',
                    duration: 2000,
                });

                this.formData = {
                    name: '',
                    email: '',
                    phone: '',
                    message: ''
                };
            } catch (error) {
                const toast = useToast();
                toast.open({
                    message: 'Error submitting form. Please try again later.',
                    type: 'error',
                    duration: 2000,
                });
            }
        }
    }
};
</script>


<style>
.style-25 {
    position: relative;
    top: 50%;
    left: 22%;
    margin-top: 35px;
    transform: translate(-50%, -50%);

    &:hover {

        .wrap,
        .text {
            &:before {
                width: 100%;
            }
        }
    }

    .wrap {
        position: relative;
        display: inline-block;
        padding: 5px 20px;
        cursor: pointer;

        &:before {
            content: "";
            width: 0%;
            height: 100%;
            position: absolute;
            background: #2980b9;
            right: 0;
            top: 0;
            transition: 0.6s;
        }
    }

    .text {
        position: relative;
        color: #34495e;
        font-family: "montserrat", sans-serif;
        font-size: 24px;
        font-weight: 900;
        text-transform: uppercase;

        &:before {
            content: attr(data-text);
            position: absolute;
            color: #fff;
            width: 0;
            overflow: hidden;
            transition: 0.6s;
        }
    }
}
</style>
