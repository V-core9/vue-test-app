<template>
  <div id="locationsContainer">
    <LocationsList v-bind:locationList="locationList" v-on:del-location-single="deleteSingleLocation"/>
    <AddLocation v-on:add-location-item="AddLocation"/>
  </div>
</template>

<script>
import LocationsList from './LocationsList.vue'
import AddLocation from './AddLocation.vue'
import axios from 'axios';
export default {
    name: 'LocationsContainer',
    components: {
        LocationsList,
        AddLocation,
    },
    data() {
        return {
        locationList: []
        }
    },
    methods: {
        deleteSingleLocation(id){
            var data = '';
            var config = {
                method: 'delete',
                url: 'http://localhost:3000/api/locations/'+id,
                headers: { },
                data : data
            };

            axios(config)
                .then(function (response) {
                    console.log(JSON.stringify(response.data));
                })
                .catch(function (error) {
                    console.log(error);
                });


            //axios.delete(`http://localhost:3000/api/locations/${id}`)
            //    .then(res => { this.locationList = this.locationList.filter(single => single.id !== id); console.log(res)})
            //    .catch(error => console.log(error));
           
        },
        AddLocation(newLocationItem){
            //const title = 'My Bathroom';
            //const category = 'AAAAA';
            //const folder = 'aruba';
            const img = 'IMG_3921-3931_Panorama.dzi';
            const start = '3921';
            const end = '3931';
            const date_taken = '1340553600';

            const{ category, title, folder } = newLocationItem;
            axios.post('http://localhost:3000/api/locations',{
                category,
                title,
                folder,
                img,
                start,
                end,
                date_taken
            })
                .then(res =>this.locationList = [...this.locationList, res.data] )
                .catch(error => console.log(error));
        }
    },
    created() {
        axios.get('http://localhost:3000/api/locations/')
            .then( res => this.locationList = res.data )
            .catch( error => console.log(error) );
    }
}
</script>