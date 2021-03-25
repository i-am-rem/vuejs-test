# Magneds VueJS Test
For this application, we want to display the contents of the JSON file you find [here](src/fixtures/pxtqu8tf3c69m4wus0t9s8wzt.json)

__The project has been left in its state that matches that of the vue-cli create command. Cleanup and remove any parts that you feel 
are not needed__

The expectations are as follows:
* Create a page for the Homepage. It can display any text.
* Create a page for the display of this design [here](./vue-magneds-test.png)  
* Introduce navigation using 'VueRouter' between the Homepage and this page.
* On the rendering of the block, introduce the ability to click on each block, and set the block to 100 value.
* Color the blocks based off their value.
    * 0 = Grey
    * 100 = Purple
* When the last block is clicked, have a modal open displaying the following message:
    * "Good job on completing your collection!"
    * The modal will close when clicking outside the modal or on the 'Close' button.
* You can use any packages from NPM that you feel are helpful in delivering the above goals.

### Nice to haves (if you want)
* Responsiveness

## Requirements
Node v15+
NPM 7.0+

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```
