<template>
    <div id="app">
        <section class="section">
            <h2>Basic Modal</h2>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure, adipisci? Itaque veritatis similique nihil id amet sapiente commodi pariatur quod quam blanditiis unde rerum exercitationem vitae, hic aspernatur quisquam!</p>
            <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ducimus atque blanditiis quas architecto vitae deserunt, nemo nisi debitis. Deserunt repellat deleniti earum officia qui possimus sapiente dolorum. Provident, consequatur nam! Lorem ipsum dolor
                sit amet consectetur adipisicing elit. Vero aut ducimus ipsam modi officiis rem consequuntur esse recusandae quo a eligendi dolore, sunt ipsa corrupti est veritatis magnam necessitatibus. Quaerat?</p>
            <p><a href="#" @click="modalOpen = true">Open the Modal</a></p>
        </section>
        <modal :title="'Whoa. A modal.'" :open="modalOpen" @close="modalOpen = false">
            <div slot="body">
                <p>This is body content. Neat.</p>
                <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Laborum illo dolores ipsum ducimus esse quidem quod molestias recusandae! Natus maiores iusto numquam tenetur non laudantium, praesentium voluptatem itaque accusantium vel?</p>
            </div>
            <div slot="footer">
                <div>
                    Footer content: <button @click="modalOpen = false">Close</button>
                </div>
            </div>
        </modal>
    </div>
</template>

<script>
    import Modal from './components/Modal.vue';
    
    export default {
        name: 'app',
        components: {
            'modal': Modal
        },
        data() {
            return {
                modalOpen: false
            }
        }
    }
</script>

<style lang="scss">
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
    }
    .section {
        width: 100%;
        max-width: 600px;
        margin: 40px auto;
    }
</style>
