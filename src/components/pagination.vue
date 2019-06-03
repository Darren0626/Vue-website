<template>
    <div class="d-flex justify-content-center">
        <nav aria-label="Page navigation example">
            <ul class="pagination">
                <li class="page-item" :class="{'disabled': !pagination.has_pre }">
                    <a class="page-link" href="#" @click.prevent="getPage(pagination.current_page - 1)" aria-label="Previous">
                        <span aria-hidden="true">&laquo;</span>
                    </a>
                </li>
                <li class="page-item" :class="{'active': pagination.current_page === page}" v-for="page in pagination.total_pages" :key="page">
                    <a class="page-link" href="#" @click.prevent="getPage(page)">{{ page }}</a>
                </li>
                <li class="page-item" :class="{'disabled': !pagination.has_next }">
                    <a class="page-link" href="#" @click.prevent="getPage(pagination.current_page + 1)" aria-label="Next">
                        <span aria-hidden="true">&raquo;</span>
                    </a>
                </li>
            </ul>
        </nav>
    </div>
</template>

<script>
    export default {
        props: {
            pagination: {
                type: Object
            }
        },
        methods: {
            getPage(page){
                this.$emit('getPage', page);
            }
        }
    }
</script>