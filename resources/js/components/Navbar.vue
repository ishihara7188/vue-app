<template>
    <nav class="navbar">
        <RouterLink class="navbar__brand" to="/">
            Vuesplash
        </RouterLink>
        <div class="navbar__menu">
            <!-- login時に表示するエリア -->
            <div v-if="isLogin" class="navbar__item">
                <button class="button">
                    <i class="icon ion-md-add"></i>
                    Submit a photo
                </button>
            </div>
            <span v-if="isLogin" class="navbar__item">
                {{ username }}
            </span>

            <!-- loginをしていない時に表示するエリア -->
            <div v-else class="navbar__item">
                <RouterLink class="button button--link" to="/login">
                    Login / Register
                </RouterLink>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    computed: {
        isLogin () {
            return this.$store.getters['auth/check']
        },
        username () {
            return this.$store.getters['auth/username']
        }
    }
}
</script>