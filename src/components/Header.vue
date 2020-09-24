<template>
    <header class="header">
        <nav class="nav">
            <g-link to="/" exact>
                <h1 class="site__name">{{ $static.metaData.siteName }}</h1>
            </g-link>
            <div>
                <h1>
                    <g-link :to="infoLink">
                        {{ isInfoPage ? "close" : "info" }}
                    </g-link>
                </h1>
            </div>
        </nav>
    </header>
</template>

<script>
export default {
    props: {
        page: {
            type: String,
            required: true
        }
    },
    computed: {
        isInfoPage() {
            return this.page === "info" && true
        },
        infoLink() {
            return this.isInfoPage ? "/" : "/info"
        }, 
    }
}
</script>

<static-query>
    query {
    metaData {
        siteName
    }
    }
</static-query>

<style>
.header h1 {
    margin-bottom: 0; 
}
  
.nav {
    padding: 1.5rem 1.25rem;
    border-bottom: 1px solid #e8ddcb;
    display: flex;
    justify-content: space-between;
    flex-direction: row;
    align-items: center;
}

.nav img {
     margin-bottom: 0;
}

@media (min-width: 320px) {
    .header .site__name {
        width: 100%;
    }
}
  
@media (min-width: 768px) {
    .header {
      height: 100vh;
      position: fixed;
      left: 0;
      top: 0;
    }

    .header .site__name {
        width: 65%;
    }
    
    .nav {
      padding: 2rem;
      width: 25vw;
      height: 100%;
      border-right: 1px solid #e8ddcb;
      border-bottom: none;
      flex-direction: column;
      align-items: flex-start;
    }
}

@media (min-width: 1024px) {
    .header .site__name {
        width: 100%;
    }
}

</style>