<template>
  <div>
    <Section id="AboutIntro" class="head space--bottom">
      <transition name="fade" appear>
        <b-container>
          <b-row>
            <b-col class="mx-auto" cols="12" lg="10">
              <article class="content">
                <h1 class="mb-4">Bienvenidos</h1>
                <p class="lead mb-4">
                  My name is Fernando Pantoja and I am well known as DJ Ferchi. I am currently working in Central & Northern New York, NYC, and South America providing DJ entertainment in clubs, restaurants, lounges, and bars with my 4000W sound system and extensive dancefloor lighting system as needed.
                  <blockquote>I provide specialized music dance party sets for the following genres: Hip Hop, Reggaeton, Salsa, Bachata, Merengue, Cumbia and Crossover.</blockquote>
                  For an awesome Latin/ hip-hop entertainment experience, email Fernando Pantoja pantojafernando@gmail.com
                </p>
              </article>
            </b-col>
          </b-row>
        </b-container>
      </transition>
    </Section>

    <transition name="fade" appear style="transition-delay: 350ms;">
      <Section id="AboutHero">
        <b-container fluid>
          <b-row>
            <b-col :cols="12">
              <figure :style="{ position: 'relative', paddingTop: paddingTop }">
                <lazy-image
                  alt="Team image"
                  class="position-absolute"
                  style="top: 0; left: 0;"
                  :lazy-srcset="image.srcSet"
                  :placeholder="image.placeholder"
                  :lazy-src="image.src"
                  :width="image.width"
                  :height="image.height"
                />
                <figcaption>
                  <p class="text-center text-muted font-weight-light">
                    <small>
                      <i>
                        Fernando Pantoja, DJ Ferchi
                      </i>
                    </small>
                  </p>
                </figcaption>
              </figure>
            </b-col>
          </b-row>
        </b-container>
      </Section>
    </transition>

    <transition name="fade" style="transition-delay: 350ms;">
      <Section id="AboutInfo" class="space--top--half">
        <b-container>
          <b-row>
            <b-col class="mx-auto" cols="12" lg="10">
              <article class="content">
                <p>
                  DJFERCHI entertainment. Disco móvil DJ. I’m proud to be your professional Móvil DJ service and source for wedding & event entertainment in Central & Northern NY. DJ Services Are Perfect For: * Weddings * Birthdays * Sweet 15's & 16's * Anniversaries * Graduations *Clubs. * Lounge. *Restaurant. * Bar. *Bachelor. *Patio Pool BBQ. *In & Out of USA. 
                </p>

                <blockquote class="blockquote">
                  <p class="mb-2">
                  Comenzando el Nuevo año con buenos proyectos, Ahora a nivel nacional eh internacional DJFERCHI entertainment. Servicio completo y pro. Para *Matrimonio *Cumpleanos *Aniversarios *Graduaciones *Fiestas patronales *Clubs. *Lounge. *Restaurante. *Bar. *Despedidas de solteros. *Piscina y BBQ Parties. *Dentro y fuera del país.                  </p>
                  <footer class="blockquote-footer">
                    DJ,
                    <cite title="Ferchi">Ferchi</cite>
                  </footer>
                </blockquote>

        
              </article>
            </b-col>
          </b-row>
        </b-container>
      </Section>
    </transition>

    <transition name="fade" style="transition-delay: 950ms;">
      <Section id="AboutClients" class="space--top--half space--bottom">
        <b-container>
          <div class="content">
            <p class="text-center mb-4">
              <i>
                You can see some of our partners below, would you like to join
                us?
              </i>
            </p>
          </div>
          <clients-logo />
        </b-container>
      </Section>
    </transition>

    <Section id="AboutTestimonials" class="bg-light space--top space--bottom">
      <b-container class="py-4">
        <b-row class="mb-3 pb-2">
          <b-col class="text-center">
            <h2 class="h5">Trusted by Users All Over the World</h2>
          </b-col>
        </b-row>
        <Testimonials :testimonials="testimonials" />
      </b-container>
    </Section>

    <!-- <section id="WorkingProcess" class="mt-4 pt-4">
      <b-container>
        <WorkingProcess />
      </b-container>
    </section> -->

    <Section id="contactForm" class="space">
      <b-container>
        <b-row class="my-4">
          <b-col :cols="12" :offset="0" :lg="6" :offset-lg="3">
            <div class="mb-4">
              <h3 class="h2">Get in Touch</h3>
              <p class="lead">Have any questions?</p>
            </div>
            <ContactForm />
          </b-col>
        </b-row>
      </b-container>
    </Section>
  </div>
</template>
<script>
const PhotoOne = () => import('https://www.datocms-assets.com/60992/1641703943-djferchi2e-2xl.png?auto=format&crop=faces&dpr=0.75&fit=crop&h=540&w=360')

export default {
  name: 'About',
  layout: 'main',
  components: {
    LazyImage: () => import('~/components/LazyImage.vue'),
    // WorkingProcess: () => import('~/components/WorkingProcess.vue'),
    ClientsLogo: () => import('~/components/ClientsLogo.vue'),
    Testimonials: () => import('~/components/Testimonials.vue'),
    ContactForm: () => import('~/components/ContactForm.vue'),
    Section: () => import('~/components/Section.vue')
  },
  async asyncData(context) {
    const image = await PhotoOne().then((M) => M)
    const paddingTop = `calc(${image.height} / ${image.width} * 100%)`
    // const logos = await Logos().then((L) => L)
    // console.log('logos', logos)
    return { image, paddingTop }
  },
  data() {
    return {
      pageTitle: 'About',
      pageDescription:
        'Proud to be your professional Móvil DJ service and source for wedding & event entertainment in Central & Northern NY. DJ Services Are Perfect For: * Weddings * Birthdays * Sweet 15s & 16s * Anniversaries * Graduations *Clubs. * Lounge. *Restaurant. * Bar. *Bachelor. *Patio Pool BBQ. *In & Out of USA.',
      testimonials: [
        {
          name: 'Happy patron',
          image: () => require('~/assets/images/client3.jpg'),
          company: 'Netflix',
          occupation: 'Sales Manager',
          body:
            "DJ Ferchi rocked our party beyond belief. C."
        },
        {
          name: 'Satisfied customer',
          image: () => require('~/assets/images/client1.jpg'),
          company: 'Umbrella Inc.',
          occupation: 'Sales Engineer',
          body:
            "Create a night to remember. Get our and see or book DJ Ferchi! Life gets better and better."
        },
        {
          name: 'Amigo en Pasaje',
          image: () => require('~/assets/images/client2.jpg'),
          company: 'ACME',
          occupation: 'Founder',
          body:
            "Ferchi esta de Pasaje, Ecuador un artiste del mundo con corozon en Ecuador y New York."
        }
      ]
    }
  },
  head() {
    return {
      title: this.pageTitle,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.pageDescription
        },
        { hid: 'og:title', name: 'og:title', content: this.pageTitle },
        {
          hid: 'og:description',
          name: 'og:description',
          content: this.pageDescription
        },
        {
          hid: 'og:image',
          name: 'og:image',
          content: this.image.images.slice(-1).pop().path || ''
        },
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.pageTitle
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: this.pageDescription
        },
        {
          hid: 'twitter:image',
          name: 'twitter:image',
          content: this.image.images.slice(-1).pop().path || ''
        }
      ]
    }
  }
}
</script>
