<template>
    <!-- ======= About us Section Start ======= -->
    <section id="aboutus_section" class="sec">
        <div class="container">
            <div class="section-title text-center mb-30">
                <span class="title-tag">KNOW MORE</span>
                <h2 class="title">About Us</h2>
            </div>
            <div class="row">
                <div class="col-lg-6">
                    <img :src="AboutImg" class="img-fluid animated" alt="about section image" loading="lazy">
                </div>
                <div class="col-lg-6 d-flex flex-column justify-content-center pt-4 pt-lg-0 gap-4 about_content">
                    <h2>Better Solutions For Your Business</h2>
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. In placerat dignissim quam, in pretium
                        velit
                        aliquet a. Proin in iaculis purus. Praesent augue purus, congue ut lectus ut, aliquet imperdiet
                        justo. Proin fermentum enim porta condimentum lacinia. Curabitur consectetur varius dapibus.
                        Cras
                        sed pulvinar velit. Vivamus accumsan scelerisque arcu, at ultrices eros sagittis a. Maecenas
                        vitae
                        quam magna. Aliquam sed massa augue. Vivamus consectetur a nisl non iaculis. Aliquam ut dictum
                        odio.
                    </p>
                    <div class="d-flex justify-content-center justify-content-lg-start">
                        <div class="linkWrap">
                            <a class="style-23" href="">
                                <span>Read More</span>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- ======= About us Section End ======= -->
</template>
<script>
import AboutImg from "../../../public/images/about_us.jpg"

export default {
    data() {
        return {
            AboutImg
        }
    }
}
</script>
<style>
.about_content h1 {
    font-size: 41px;
    font-weight: 900;
}

.style-23 {
    position: relative;
    z-index: 9;
    padding: 20px 20px;
    color: #000;
    font-size: 18px;
    font-weight: bold;
    text-decoration: none;
    border-radius: 50px;

    &:hover {
        &:before {
            background: #3e6dd1;
            width: 100%;
        }
    }

    &:before {
        content: '';
        position: absolute;
        z-index: 1;
        top: 0;
        left: 0;
        width: 25%;
        height: 100%;
        border-radius: 50px;
        background: #fd5724;
        transition: all 0.85s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    }

    span {
        position: relative;
        z-index: 2;
        color: #000;
    }
}
</style>