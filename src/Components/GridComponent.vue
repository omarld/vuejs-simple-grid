<template>
    <div class="grid-container" id="data-list">

        <div class="mdl-card mdl-shadow--2d">
            <div class="mdl-card__title mdl-card--expand table-menu">
                <div class="row">
                    <div class="col-md-6">
                        <h2 class="mdl-card__title-text">Root</h2>
                    </div>

                    <div class="right-header-menu col-md-6">

                        <!-- Right aligned menu below button -->
                        <div class="float-right">
                            <button id="demo-menu-lower-right"
                                    class="mdl-button mdl-js-button mdl-button--icon">
                              <i class="material-icons">more_vert</i>
                            </button>

                            <ul class="mdl-menu mdl-menu--bottom-right mdl-js-menu mdl-js-ripple-effect"
                                for="demo-menu-lower-right">
                              <li class="mdl-menu__item">Some Action</li>
                              <li class="mdl-menu__item">Another Action</li>
                              <li disabled class="mdl-menu__item">Disabled Action</li>
                              <li class="mdl-menu__item">Yet Another Action</li>
                            </ul>
                        </div>
                        <input name="query" class="search float-right" placeholder="Search">

                    </div>

                </div>

            </div>
            <div class="mdl-card__supporting-text table-content">
                <table  class="table-container mdl-data-table mdl-js-data-table mdl-data-table--selectable full-width no-border">
                    <thead clas="mdl-data-table__cell--non-numeric">
                        <tr>
                            <th v-for="key in columns" :class="[key.class]">
                                <span class="sort" v-bind:data-sort="key.name" @click="toggleSort($event)">{{key.name}}</span>
                            </th>
                        </tr>
                    </thead>
                    <tbody class="list">
                        <tr v-for="entry in data">
                            <td v-for="key in columns" :class="[key.class, key.name]">
                                <span v-html="getFieldValue(key, entry[key.name])"></span>
                            </td>
                        </tr>
                    </tbody>

                </table>
            </div>
        </div>

    </div>

</template>

<script>

    import MaterialDesign from 'mdl/material.min.js';

    export default {
        name: 'GridComponent',
        props: {
           data: Array,
           columns: Array,
           filterKey: String
         },

        data(){
            return {
              sortOrders: ''
            }
        },

        mounted(){
            console.log("mounted..");
            var listOptions = {
                valueNames: [ "Thumbnail", "FileName", "FileType", "FileSize", "TimeStamp"]
            };
            debugger;
            var tableView = new List('data-list', listOptions);
        },

        computed: {

          },

        filters: {
            capitalize: function (str) {
              return str.charAt(0).toUpperCase() + str.slice(1);
            }
        },

        methods: {
            toggleSort(evt) {
                var $currentTarget = $(evt.currentTarget);

                $("th[class*=mdl-data-table__header--sorted]").removeClass("mdl-data-table__header--sorted-ascending");
                $("th[class*=mdl-data-table__header--sorted]").removeClass("mdl-data-table__header--sorted-descending");

                if($currentTarget.hasClass("asc")){
                    $currentTarget.parent().removeClass("mdl-data-table__header--sorted-ascending");
                    $currentTarget.parent().addClass("mdl-data-table__header--sorted-descending");
                } else if($currentTarget.hasClass("desc")){
                    $currentTarget.parent().removeClass("mdl-data-table__header--sorted-descending");
                    $currentTarget.parent().addClass("mdl-data-table__header--sorted-ascending");
                } else {
                    $currentTarget.parent().addClass("mdl-data-table__header--sorted-ascending");
                }
            },
            getFieldValue: function(key, value){
                if(!key){
                    return "";
                }
                if(key && key.type === "image"){
                    let imageHtml= "<img src=\"" + value + "\" />";
                    return imageHtml;
                } else {
                    return value;
                }
            }
        }
    }

</script>

<style>

.grid-container .mdl-card {
    width: 1100px;
}

.grid-container {
    position: relative;
    height:100vh;
    width: 90%;
    margin: 5% 5%;
    text-align: center;
}

.grid-container table thead tr th {
    /*font-variant: small-caps;*/
}

.table-container tr th span:hover{
    cursor: pointer;
}

.align-middle {
    display: inline;
    vertical-align: middle;
}

.full-width {
    width: 100%;
}

.mdl-data-table tbody tr {
    height: 100px;
}

.mdl-data-table tbody tr td span img {
    position: relative;
    width: 75px;
    height: auto;
    border: 1px solid grey;
}

.table-menu-section {
    position: relative;
    height: 100px;
    width: 100%;
    background-color: #fff;
}

.mdl-cell {
    margin: 0;
}

.mdl-card__supporting-text {
    padding: 0;
}

.no-border {
    border: 0;
}

tabe {
    position: relative;
}

.table-menu {
    padding-left: 24px;
}

.table-menu .row{
    width: 100%;
    height: auto;
}


.table-content {
    width: 1200px;
}

.mdl-data-table td:first-of-type, .mdl-data-table th:first-of-type {
    padding-left: 0px;
}

.float-right {
    float: right;
}

.right-header-menu div {
    display:inline-block;
}



</style>
