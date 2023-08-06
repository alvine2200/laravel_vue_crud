<template>
    <div class="container my-5">
        <div class="container-fluid">
            <div class="mx-auto">
                <RouterLink class="btn btn-primary float-end" to="/students">Back</RouterLink>
            </div>

            <ul class="alert alert-warning d-flex flex-wrap text-center" v-if="Object.keys(this.errorList).length > 0">
                <li class="mb-2 " v-for="(error, index) in this.errorList" :key="index">
                    {{ error[0] }}
                </li>
            </ul>
            <div class="row pt-5">
                <div class="col-md-12">
                    <form class="group">
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <label for="name">Name</label>
                                <input type="text" v-model="model.students.name" class="form-control" placeholder="Name">
                            </div>
                            <div class="col-md-6 mb-3">
                                <label for="email">Email</label>
                                <input type="text" v-model="model.students.email" class="form-control" placeholder="Email">
                            </div>
                            <div class="col-md-6 mb-3">
                                <label for="class">Course</label>
                                <input type="text" v-model="model.students.course" class="form-control"
                                    placeholder="Course">
                            </div>
                            <div class="col-md-6 mb-3">
                                <label for="class">Class</label>
                                <input type="text" v-model="model.students.class" class="form-control" placeholder="Class">
                            </div>
                            <div class="col-md-6 mb-3">
                                <label for="name">Year</label>
                                <input type="month" v-model="model.students.year" class="form-control" placeholder="Year">
                            </div>
                            <div class="m-3">
                                <button type="button" @click="saveStudent" class="btn btn-primary">Submit</button>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'add_Students',
    data() {
        return {
            model: {
                errorList: "",
                students: {
                    name: '',
                    email: '',
                    course: '',
                    class: '',
                    year: '',
                }
            }
        }
    },
    methods: {
        saveStudent() {
            var mythis=this;
            axios.post('http:127.0.0.1:8000/api/students/create', $this.model.students)
                .then(res => {
                    if (res.status == 'success') {
                        console.log(res);
                        this.students = {
                            name: '',
                            email: '',
                            course: '',
                            class: '',
                            year: '',
                        }
                        this.errorList="";
                        alert('Success: Student Added successfully');
                    } else {
                        console.log(res)
                        this.students = {
                            name: '',
                            email: '',
                            course: '',
                            class: '',
                            year: '',
                        }
                        alert('Error: Someting Went Wrong');
                    }
                })
                .catch(function(error){
                    if(error.response){
                        mythis.errorList=error.response.data.errors;
                        console.log(error.response)
                    }else if (error.request) {
                        console.log(error.request)
                    }else{
                        console.log(error)
                    }
                })
        }
    }
}
</script>