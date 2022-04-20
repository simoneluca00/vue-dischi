<template>
    <div class="loading">
        <div class="spinner"></div>
        <h4>Playlists are loading...</h4>
    </div>
</template>

<script>
    export default {
        name: 'LoaderComp',

    }
</script>


<style scoped lang="scss">
    .loading {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        height: 90vh;

        h4 {
            color: #f3f3f3;
            margin-top: 10px;
        }

        .spinner {
            border: 12px solid #3498db;
            border-top: 12px solid #f3f3f3;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            animation: spin 2s linear infinite;

        }

        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }

            100% {
                transform: rotate(360deg);
            }
        }
    }
</style>