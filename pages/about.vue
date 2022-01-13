<template>
  <div>
    <Section id="AboutIntro" class="head space--bottom">
      <transition name="fade" appear>
        <b-container>
          <b-row>
            <b-col class="mx-auto" cols="12" lg="10">
              <article class="content">
                <h1 class="mb-4">About</h1>
                <p class="lead mb-4">
                  DJ Ferchi 
                  committed to providing you with
                  the best live entertainment
                  service and customer satisfaction.
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
                        Fernando Pantoja, DJ Ferchi  January 2022
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
                  DJ Ferchi rocked our party beyond belief!
                </p>

                <blockquote class="blockquote">
                  <p class="mb-2">
                    Create a night to remember. Get out and see DJ Ferchi live! Life gets better and better!
                  </p>
                  <footer class="blockquote-footer">
                    Fan,
                    <cite title="Aaron Siskind">Citizen of the Musicverse</cite>
                  </footer>
                </blockquote>

		<p>
                    DJ Ferchi Entertainment. Disco Movil DJ. I'm proud to be your professional Movil DJ service and source for wedding & event entertainment in Central and Northern New York.  DJ Services are perfect for:
		<ul>
			<li>Weddings</li>
			<li>Birthdays</li>
			<li>Sweet 15's & 15's</li>
			<li>Anniversaries</li>
			<li>Graduations</li>
			<li>Clubs</li>
			<li>Lounge</li>
			<li>Restaurant</li>
			<li>Bar</li>
			<li>Bachelor</li>
			<li>Patio Pool BBQ</li>
			<li>* In & Out of USA</li>
                </ul>
		</p>
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
               Call DJ Ferchi to book an unforgettable experience. 315-566-9138
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
              <h3 class="h2">Contact DJ Ferchi</h3>
              <p class="lead">Please share your thoughts</p>
            </div>
            <ContactForm />
          </b-col>
        </b-row>
      </b-container>
    </Section>
  </div>
</template>
<script>
const PhotoOne = () => import('~/assets/images/persone-1.jpg')

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
        'Welcome to DJFerchi.com.  We are working to provide a good user experience. Please let us know if you see anything out of place.',
      testimonials: [
        {
          name: 'Happy Patron',
          image: () => require('~/assets/images/client3.jpg'),
          company: 'Undisclosed Client',
          occupation: 'Booking Agent',
          body:
            "DJ Ferchi rocked our party beyond belief."
        },
        {
          name: 'Satisfied Customer',
          image: () => require('~/assets/images/client1.jpg'),
          company: 'Professional Contact',
          occupation: 'Music Industry',
          body:
            "Create a night to remember.  Get out and see or book DJ Ferchi! Life gets better and better."
        },
        {
          name: 'Amigo en Pasaje',
          image: () => require('~/assets/images/client2.jpg'),
          company: 'Ecuador',
          occupation: 'Founder',
          body:
            "Ferchi esta de Pesaje, Ecuador con un corozon del mundo. Muy professional y mumbatonado."
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
