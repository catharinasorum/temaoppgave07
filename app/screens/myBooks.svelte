<script>
    import FirestoreParser from 'firestore-parser'

    let books = []
    const baseUrl = 'https://firestore.googleapis.com/v1/'
    const booksUrl = baseUrl + 'projects/svelte-native-firebase/databases/(default)/documents/books'

    const getBooks = () => {
        fetch(booksUrl)
            .then (response => response.json() )
                .then ( parsed => {
                    books = parsed.documents
                })
            .catch (error => console.log(error))
    }

    getBooks()
</script>

<page>
    <actionBar hidden={true} />
    <scrollView class="main">
        <stackLayout>
        {#each books as book}
             <flexboxLayout class="book">
                <stackLayout>
                    <label class="h2" text={book.fields.title} />
                    <label class="body" text={book.fields.author} />
                </stackLayout>
             </flexboxLayout>
        {:else}
             <activityIndicator busy={true} />
        {/each}
        </stackLayout>
    </scrollView>
</page>

<style>
    .main {
        background-color: #fff;
    }
    .book {
        margin: 20;
        padding: 15;
        background-color: #eee;
        flex-direction: column;
        text-align: center;
    }

</style>
