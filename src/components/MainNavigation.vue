<script>
import * as quark from 'quark-gui';
import MainNavigationTemplate from "./MainNavigationTemplate.quark";

export default {
    name: 'MainNavigation',
    template: MainNavigationTemplate,
}
</script>

<style>
header img {
    padding: 7px 0;
    display: none;
}
.navbar-html-content{
    margin: 0;
    display: inline-block;
    vertical-align: top;
    padding: 0;
}
.navbar-select-container{
    display: inline-block;
    padding: 0;
}

.navbar-divider{
    border-left: 1px solid rgba(255, 255, 255, 0.08);
    border-right: 1px solid rgba(0, 0, 0, 0.08);
    width: 1px;
    height: 34px;
    display: inline-block;
    margin: 7px 15px;
}
/*
.navbar-select-container:after{
    font-family: FontAwesome;
    content: "\F078";
    position: relative;
    float: right;
    top: -25px;
    right: 8px;
    -moz-transition: transform 0.2s ease-in-out, top 0.2s ease-in-out;
    -o-transition: transform 0.2s ease-in-out, top 0.2s ease-in-out;
    -webkit-transition: transform 0.2s ease-in-out, top 0.2s ease-in-out;
    transition: transform 0.2s ease-in-out, top 0.2s ease-in-out;
}*/

.navbar-label{
    display: none;
    font-size: 12px;
    cursor: default;

}
.navbar-select{
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    background: none;
    color: white;
    font-size: 16px;
    border: none;
    cursor: pointer;
    height: 48px;
}
.navbar-select option{
    background-color: #f9f9f9;
    color: #333435;
}

@media (min-width: 420px){
    .navbar-html-content{
        padding: 5px 0;
    }
    .navbar-select-container{
        padding: 3px 4px;
    }
    .navbar-label{
        display: block;
    }
    .navbar-select{
        height: auto;
        width: auto;
    }
}

@media (min-width: 480px){
    header img {
        display: block;
    }
}

@media (min-width: 768px){
    .navbar-html-content{
        padding: 7px 0;
    }
    .navbar-select{
        font-size: 24px;
    }
    .navbar-label{
        font-size: 14px;
    }
    .navbar-select-container{
        padding: 3px 10px;
    }
}


</style>
