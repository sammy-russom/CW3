<template>
    
</template>
  
  <script>
  export default {
    name: 'LessonComponent',
    props: {
        subjects: Array
    },
    computed:{
        filterItems(){
            if (this.criteria != "all" & this.criteria != "availability" & this.criteria != "price") {
                return this.subjects.filter(x => x[this.criteria].toLowerCase().includes(this.searchInput)).sort((a,b)=>{
                    switch (this.order) {
                        case "ascending":
                                if(a[this.criteria] > b[this.criteria]){
                                    return 1
                                }
                                if(b[this.criteria] > a[this.criteria]){
                                    return -1
                                }
                                return 0
                        case "descending":
                            if(a[this.criteria] > b[this.criteria]){
                                return -1
                            }
                            if(b[this.criteria] > a[this.criteria]){
                                return 1
                            }
                            return 0
                    }
                })
            }
            if (this.criteria == "availability") {
                return this.subjects.filter(x => x["spaces"] > 0)
            }
            if (this.criteria == "price") {
                return this.subjects.filter(x => (x["price"]+"").includes(this.searchInput)).sort((a,b)=>{
                    switch (this.order) {
                        case "ascending":
                                if(a[this.criteria] > b[this.criteria]){
                                    return 1
                                }
                                if(b[this.criteria] > a[this.criteria]){
                                    return -1
                                }
                                return 0
                        case "descending":
                            if(a[this.criteria] > b[this.criteria]){
                                return -1
                            }
                            if(b[this.criteria] > a[this.criteria]){
                                return 1
                            }
                            return 0
                    }
                })
            }

            return this.subjects
        }
    },
    methods:{
        addToCart(subject){
            this.$emit("add-cart",JSON.stringify(subject))
        },
        removeFromCart(cart_item){
            this.$emit("remove-cart",JSON.stringify(cart_item))
        },
        submit_cart(){
            alert("Submitted cart")
        },
        checkout(){
            this.showSubjects = this.showSubjects ? false : true
        },
        changeCriteria(criteria){
            this.criteria = criteria
        },
        changeOrder(order){
            this.order = order
        }
    },
    data(){
        return{
        criteria:"lesson",
        order:"ascending",
        searchInput:"",
        }
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
   
        
        
  </style>
  