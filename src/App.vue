<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 header-text">
                <h1>Github Markdown Preview</h1>
                <h4>It's fun</h4>
            </div>
        </div>
        
        <div class="row">
            <div class="col-xs-12 col-md-6">
                <textarea id="editor" class="form-control" v-model="rawMarkdown"></textarea>
            </div>
            <div id="preview" class="col-xs-12 col-md-6">
                <div class="panel panel-default">
                    <div class="panel-body">
                        <article class="markdown-body">
                            {{renderedMarkdown}}
                        </article>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="row">
            <div class="col-xs-12">
                <button type="button" class="btn btn-primary pull-right" @click="renderPreview">
                    Preview
                </button>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
       data(){
           return {
               rawMarkdown: '',
               renderedMarkdown: ''
           }
           
       },
       methods: {
           renderPreview(){
               this.$http({
                   url: 'https://api.github.com/markdown',
                   method: 'POST',
                   data: {text: this.rawMarkdown, mode: 'markdown'}
               }).then(function(response){
                   this.renderedMarkdown = response.data;
               }, function(response){
                   console.log(response.data);
               });
           }
       }

    }
</script>

<style>

</style>
