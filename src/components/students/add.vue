<template>
    <div class="container my-5">
        <div class="container-fluid">
            <div class="mx-auto">
                <RouterLink class="btn btn-primary float-end" to="/students">Back</RouterLink>
            </div>
            <div class="row pt-5">
                <div class="col-md-12">
                    <form class="group">
                        <div class="row">
                            <div class="col-md-6 mb-3">
                                <input type="text" class="form-control" placeholder="Name">
                            </div>
                            <div class="col-md-6 mb-3">
                                <input type="text" class="form-control" placeholder="Email">
                            </div>
                            <div class="col-md-6 mb-3">
                                <input type="text" class="form-control" placeholder="Class">
                            </div>
                            <div class="col-md-6 mb-3">
                                <input type="text" class="form-control" placeholder="Year">
                            </div>
                            <div class="mb-3">
                                <button class="btn btn-primary">Add Student</button>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>