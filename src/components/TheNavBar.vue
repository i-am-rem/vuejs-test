
<template>
    <div id="nav">
        <nav class="navbar navbar-expand-md navbar-dark bg-dark">
            <div class="container-fluid">
                <a class="navbar-brand"><img src="@/assets/logo.png" width="30" height="30" class="d-inline-block align-top" alt=""></a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarTogglerDemo03" aria-controls="navbarTogglerDemo03" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
               
                <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
                    <ul class="navbar-nav me-auto mb-2 mb-md-0">
                        <li class="nav-item">
                            <router-link to="/" class="nav-link">Home</router-link>
                        </li>
                        <li class="nav-item">
                            <router-link to="/Collection" class="nav-link">Collections</router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
        <router-view/>
    </div>
</template>    
