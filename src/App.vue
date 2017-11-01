<template>
   <div>
    <div class="header clearfix">
        <nav>
            <ul class="nav nav-pills pull-right">
                <li role="presentation">
                    <a href="#" @click="currentView='managePosts'">Manage Posts</a>
                </li>
                <li role="presentation">
                    <a href="#" @click="currentView='createPost'">Create Post</a>
                </li>
            </ul>
        </nav>
        <h3 class="text-muted">Admin Panel</h3>
    </div>
    
    <div class="container">
        <keep-alive>
            <component :is="currentView"></component>
        </keep-alive>
    </div>
 </div>
</template>

<script>
    import ManagePosts from './components/Manage-Posts.vue'
    import CreatePost from './components/Create-Post.vue'
    export default {
       data(){
           return {
               currentView: 'managePosts'
           }
       },
       components: {
           managePosts: ManagePosts,
           createPost: CreatePost
       }
    }
</script>

<style>

</style>
