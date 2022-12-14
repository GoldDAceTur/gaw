<template>
    <div>
        <h2 id="tutorials">
            Listing all tutorials for a library on cdnjs
        </h2>
        <div class="doc">
            <p>
                The <code>/libraries/:library/tutorials</code> endpoint returns a JSON array containing all the
                user-submitted tutorials relating to this library on cdnjs. This is a mirror of the
                <code>tutorials</code> property returned from the main library endpoint.
            </p>
            <p>
                The cache lifetime on this endpoint is 24 hours.
            </p>
            <p>
                <small>
                    <i>
                        Alongside the properties listed here, there may be other optional properties available based on
                        the metadata available in each source tutorial file.
                    </i>
                </small>
            </p>

            <h3>Query Parameters</h3>
            <table>
                <thead>
                    <tr>
                        <th>Parameter</th>
                        <th>Type</th>
                        <th>Required</th>
                        <th>Description</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="field in query">
                        <td><code class="key">{{ field.param }}</code></td>
                        <td><code class="key">{{ field.type }}</code></td>
                        <td><code class="key">{{ field.req ? 'required' : 'optional' }}</code></td>
                        <td>
                            <p v-for="desc in field.desc" v-html="desc"></p>
                        </td>
                    </tr>
                </tbody>
            </table>

            <h3>JSON Response</h3>
            <table>
                <thead>
                    <tr>
                        <th>Property</th>
                        <th>Type</th>
                        <th>Description</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="field in response">
                        <td><code class="key">{{ field.prop }}</code></td>
                        <td>
                            <template v-for="type in field.type">
                                <code class="key">{{ type }}</code>&nbsp;
                            </template>
                        </td>
                        <td>
                            <p v-for="desc in field.desc" v-html="desc"></p>
                        </td>
                    </tr>
                </tbody>
            </table>

            <h3>Example Requests</h3>

            <h4>
                <a href="https://api.cdnjs.com/libraries/vue/tutorials">
                    <code class="key">https://api.cdnjs.com/libraries/vue/tutorials</code>
                </a>
            </h4>
            <JSONExample>[{"id":"wtf-is-vuex","modified":"2017-05-29T04:18:13.000Z","author":{"name":"Anthony","email":"anthony@vuejsdevelopers.com","description":"Web developer, author and online course instructor with Vue.js Developers","homepage":"http://vuejsdevelopers.com","twitter":"https://twitter.com/vuejsdevelopers"},"description":"Vuex is one of the most useful tools in the Vue.js ecosystem, but it can be very confusing at first. I've written this primer on Vuex to give you the background that I wish I'd had.","homepage":"http://vuejsdevelopers.com","keywords":["vue.js","vuex"],"library-tags":["vue.js","vuex"],"name":"WTF is Vuex? A Beginner's Guide To Vue's Application Data Store","repository":"https://github.com/vuejsdevelopers","content":"Vuex. Is it pronounced ???vewks???, or ???veweks???? Or maybe it???s meant to be ???vew???, pronounced with a French-style silent ???x????\n\nMy trouble with understanding Vuex only began with the name.\n\nBeing an eager Vue developer I???d heard enough about Vuex to suspect that it must be an important part of the Vue ecosystem, even if I didn???t know what it actually was.\n\nI eventually had enough of wondering, so I went to the documentation with plans of a brief skim through; just enough to get the idea.\n\nTo my chagrin I was greeted with unfamiliar terms like ???state management pattern???, ???global singleton??? and ???source of truth???. These terms may make sense to anyone already familiar with the concept, but for me they didn???t gel at all.\n\nThe one thing I did get, though, was that Vuex had something to do with Flux and Redux. I didn???t know what those were either, but I figured it may help if I investigated them first.\n\nAfter a bit of research and persistence the concepts behind the jargon finally started to materialise in my mind. I was getting it. I went back to the Vuex documentation and it finally hit me???Vuex is freaking awesome!\n\nI???m still not quite sure how to pronounce it, but Vuex has become an essential piece in my Vue.js toolbelt. I think it???s totally worth your time to check it out too, so I???ve written this primer on Vuex to give you the background that I wish I???d had.\n\nNote: This article was originally posted [here on the Vue.js Developers blog](http://vuejsdevelopers.com/2017/05/15/vue-js-what-is-vuex/?jsdojo_id=cjs_wfv) on 2017/05/15 ..."}]</JSONExample>
            <p>
                <small>
                    <i>Example response has been trimmed to remove text from tutorial content.</i>
                </small>
            </p>

            <h4>
                <a href="https://api.cdnjs.com/libraries/backbone.js/tutorials?fields=name,modified">
                    <code class="key">https://api.cdnjs.com/libraries/backbone.js/tutorials?fields=name,modified</code>
                </a>
            </h4>
            <JSONExample>[{"id":"cross-domain-sessions","name":"Cross-domain Backbone.js with sessions using CORS","modified":"2017-09-05T17:41:17.000Z"},{"id":"infinite-scrolling","name":"Lightweight Infinite Scrolling using Twitter API","modified":"2017-09-05T17:41:17.000Z"},{"id":"nodejs-restify-mongodb-mongoose","name":"Simple example - Node.js, Restify, MongoDb and Mongoose ","modified":"2017-09-05T17:41:17.000Z"},{"id":"organizing-backbone-using-modules","name":"Organizing your application using Modules (require.js)","modified":"2017-09-05T17:41:17.000Z"},{"id":"real-time-backbone-with-pubnub","name":"Real-Time Backbone With PubNub","modified":"2018-07-28T08:54:41.000Z"},{"id":"seo-for-single-page-apps","name":"SEO for single page apps","modified":"2017-09-05T17:41:17.000Z"},{"id":"what-is-a-collection","name":"What is a collection?","modified":"2017-09-05T17:41:17.000Z"},{"id":"what-is-a-model","name":"What is a model?","modified":"2017-09-05T17:41:17.000Z"},{"id":"what-is-a-router","name":"What is a router?","modified":"2017-09-05T17:41:17.000Z"},{"id":"what-is-a-view","name":"What is a view?","modified":"2017-09-05T17:41:17.000Z"},{"id":"why-would-you-use-backbone","name":"Why do you need Backbone.js?","modified":"2017-09-05T17:41:17.000Z"}]</JSONExample>
        </div>
    </div>
</template>

<script>
    import JSONExample from '../json_example';

    export default {
        name: 'APITutorials',
        components: {
            JSONExample,
        },
        data () {
            return {
                query: [
                    {
                        param: 'fields',
                        type: 'comma-separated string',
                        req: false,
                        desc: [
                            'Provide a comma-separated string of fields to return for each tutorial object in the array.',
                            'The <code>id</code> property will always be present in every object to allow for identification of each tutorial in the array.',
                        ],
                    },
                    {
                        param: 'output',
                        type: 'string',
                        req: false,
                        desc: [
                            'Use the output value <code>human</code> to receive the JSON results in pretty print format, presented on a HTML page.',
                        ],
                    },
                ],
                response: [
                    {
                        prop: '[].id',
                        type: [
                            'string',
                        ],
                        desc: [
                            'The slug/identifier for the tutorial, based on the filename of the tutorial in cdnjs/tutorials.',
                            '<small><i>This is the id that should be used when accessing the <code>/libraries/:library/tutorials/:tutorial</code> API endpoint.</i></small>',
                        ],
                    },
                    {
                        prop: '[].modified',
                        type: [
                            'string',
                        ],
                        desc: [
                            'The timestamp of when the tutorial was last modified, in ISO 8601 format.',
                            'This is based on the last commit that touched the tutorial in cdnjs/tutorials.',
                        ],
                    },
                    {
                        prop: '[].created',
                        type: [
                            'string',
                        ],
                        desc: [
                            'The timestamp of when the tutorial was first published, in ISO 8601 format.',
                            'This is based on the first commit where the tutorial was added in cdnjs/tutorials.',
                        ],
                    },
                    {
                        prop: '[].name',
                        type: [
                            'string',
                        ],
                        desc: [
                            'The title/name for the tutorial.',
                        ],
                    },
                    {
                        prop: '[].content',
                        type: [
                            'string',
                        ],
                        desc: [
                            'The raw markdown content for the tutorial.',
                        ],
                    },
                ],
            };
        },
    };
</script>
