<template>
    <div class="container">
        <div class="p-4">
            <div class="row">
                <div class="row">
                    <h3>Roles</h3>
                </div>
                <div class="table-responsive">
                    <table class="table table-bordered border-primary">
                        <thead class="table-primary">
                            <tr>
                                <th scope="col"># </th>
                                <th scope="col">Rol</th>
                                
                                <!-- <th scope="col">Accion </th> -->
                            </tr>
                        </thead>
                        <tbody class="text-secondary">
                            <tr v-for="(item, index) in Roles" :key="index">
                                <th scope="row">{{ index +1 }}</th>
                                <td>{{ item.role }}</td>
                                <!-- <td>
                                    <button type="button" class="btn btn-outline-warning " data-bs-toggle="modal"
                                        data-bs-target="#EditarModal">
                                        Editar
                                    </button>
                                </td> -->
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            Roles: []
        }
    },
    mounted() {
        this.listarRoles() 
        
    },
    methods: {
        listarRoles() {
            this.axios.get('/Roles', { 'headers': { 'Authorization': `Bearer ${localStorage.getItem('token')}` } })
                .then((response) => {
                    console.log(response.data)
                    this.Roles = response.data.data;
                })
                .catch((e) => {
                    console.log('error' + e);
                })
        }
    },
}
</script>