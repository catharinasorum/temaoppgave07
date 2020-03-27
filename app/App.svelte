<script>
    import { registerNativeViewElement } from 'svelte-native/dom'

    registerNativeViewElement("cardView", () => require("@nstudio/nativescript-cardview").CardView);

    import addBooks from './screens/addBooks.svelte'
    import myBooks from './screens/myBooks.svelte'
    import bookList from './screens/bookList.svelte'

    let selectedTab = 1
</script>

<page actionBarHidden={true}>
    <bookList />
    <page actionBarHidden={true}>
    <tabs bind:selectedIndex={selectedTab} tabsPosition="bottom">
        <tabStrip>
            <tabStripItem>
                <label text="add books" />
            </tabStripItem>
            <tabStripItem>
                <label text="my books" />
            </tabStripItem>
            <tabStripItem>
                <label text="booklist" />
            </tabStripItem>
        </tabStrip>

        <tabContentItem>
            <cardView margin="32" elevation="40" shadowOffsetWidth="0" radius="24" shadowColor="#555555">
                <Page1 />
            </cardView>
        </tabContentItem>
        <tabContentItem>
            <cardView margin="32" elevation="40" shadowOffsetWidth="0" radius="24" shadowColor="#555555">
                <Page2 bind:selectedTab={selectedTab}/>
            </cardView>
        </tabContentItem>

        <tabContentItem>
            <cardView margin="32" elevation="40" shadowOffsetWidth="0" radius="24" shadowColor="#555555">
                <Page3 />
            </cardView>
        </tabContentItem>

    </tabs>
</page>