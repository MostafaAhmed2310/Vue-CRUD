<template>
    <div class="modal fade" :id="id" tabindex="-1" aria-labelledby="viewUserModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="viewUserModalLabel">{{type == 'view' ? "View User" : type == 'edit' ? "Edit User" : type == 'add' ? "Add New User" : "Delete User"}}</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <p v-if="type == 'delete'">Are You Sure ?</p>
                    <form v-if="type !== 'delete'">
                        <div class="mb-3">
                            <img class="details-profile-pic" :src="viewingUser.profile_picture"/>
                        </div>
                        <div class="mb-3">
                            <label for="f_name" class="form-label">Frist Name</label>
                            <input type="text" class="form-control" id="f_name" v-model="viewingUser.first_name" :disabled="type == 'view' ? true : false" required>
                        </div>
                        <div class="mb-3">
                            <label for="l_name" class="form-label">Last Name</label>
                            <input type="text" class="form-control" id="l_name" v-model="viewingUser.last_name" :disabled="type == 'view' ? true : false">
                        </div>
                        <div class="mb-3">
                            <label for="email" class="form-label">Email</label>
                            <input type="email" class="form-control" id="email" v-model="viewingUser.email" :disabled="type == 'view' ? true : false">
                        </div>
                        <div class="mb-3">
                            <label for="phone" class="form-label">Phone Number</label>
                            <input type="text" class="form-control" id="phone" v-model="viewingUser.phone" :disabled="type == 'view' ? true : false">
                        </div>
                        <div class="mb-3">
                            <label for="description" class="form-label">Description</label>
                            <QuillEditor contentType="html" v-model:content="viewingUser.desc" theme="snow" :read-only="type == 'view' ? true : false"/>
                        </div>
                        <div class="modal-footer">
                            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                            <button v-if="type == 'edit'" type="submit" class="btn btn-primary">Edit</button>
                            <button v-if="type == 'add'" type="submit" class="btn btn-primary" @click="this.$emit('addNewUser', viewingUser)">Add</button>
                        </div>
                    </form>
                </div>
                <div class="modal-footer" v-if="type == 'delete'">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                    <button data-bs-dismiss="modal" @click="this.$emit('deleteUser', viewingUser.id)" type="button" class="btn btn-danger">Delete</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { QuillEditor } from '@vueup/vue-quill'
import '@vueup/vue-quill/dist/vue-quill.snow.css';

export default {
    name: 'MainModal',
    components:{
        QuillEditor
    },
    props: {
        id: String,
        type: String,
        user: Object
    },
    data(){
        return{
            viewingUser: {
                first_name: "",
                last_name: "",
                email: "",
                phone: "",
                profile_picture: "",
                desc: ""
            },
            
        }
    },
    methods:{},
    mounted(){},
    updated(){
        if(this.type !== 'add'){
            this.viewingUser = JSON.parse(JSON.stringify(this.user));
        }
    }
}
</script>

<style scoped>
.details-profile-pic{
    width: 100px;
    height: 100px;
    border-radius: 50%;
    margin: auto;
    display: block;
    box-shadow: 1px 1px 4px 1px #ddd
}
</style>
