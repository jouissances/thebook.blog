<template>
    <Layout page="info">
        <section class="info__blurb">
                <div v-html="data.description"></div>
                <div v-html="data.cta"></div>
            <ul>
                <li>
                    <p>
                        <a :href="`mailto:${data.contact.email}`">
                            Email: {{ data.contact.email}}
                        </a>
                    </p>
                </li>
                <li>
                    <p>
                        <a :href="`https://goodreads.com/${data.contact.goodreads_handle}`">
                            Goodreads: @{{ data.contact.goodreads_handle}}
                        </a>
                    </p>
                </li>
                <li>
                    <p>
                        <a :href="`https://tumblr.com/${data.contact.tumblr_handle}`">
                            Tumblr: @{{ data.contact.tumblr_handle}}
                        </a>
                    </p>
                </li>
                <li>
                    <p>
                        <a :href="`https://github.com/${data.contact.github_handle}`">
                            Github: {{ data.contact.github_handle }}
                        </a>
                    </p>
                </li>
            </ul>
        </section>
    </Layout>
</template>

<script>
    export default {
      metaInfo() {
          return {
            title: "Info",
            bodyAttrs: {
                style: `background-color: ${this.data.background_color}; color: ${this.data.text_color}`
            }
          }
      },
      computed: {
          data: function() {
              return this.$page.metaData.infoData
          }
      }
    }
</script>

<page-query>
    query getInfoPageData {
        metaData {
            infoData {
                description
                cta 
                contact {
                    email
                    goodreads_handle
                    tumblr_handle
                    github_handle
                }
                background_color
                text_color
            }
        }
    }
</page-query>

<style lang="scss">
    .info__blurb {
        max-width: 800px;
        padding: 1.5rem 1.25rem;
        p {
            font-size: 1.4rem;
        }
    }

    @media (min-width: 768px) {
        .info__blurb {
            padding: 2rem;
        }
    }

    @media(min-width: 1440px) {
        .info__blurb {
            padding: 3rem;
        }
    }
</style>
