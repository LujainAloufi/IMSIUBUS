# IMSIUBUS
IMSIU Transportation System Project
import wixData from 'wix-data';

let debounceTimer;

$w.onReady(() => {

   $w("#input1").onKeyPress(function () {

       $w("#vectorImage1").show();

       $w("#input1").value;

       if (debounceTimer) {
           clearTimeout(debounceTimer);
           debounceTimer = undefined;
       }
       debounceTimer = setTimeout(() => {
           filter($w("#input1").value);
       }, 200);

   })

   let searchWord;

   function filter(search) {
       if (searchWord !== search) {
           $w("#dataset1").setFilter(wixData.filter().contains('serviceName', search)
                   .or(wixData.filter().contains("slug", search))
                   //Insert more field filter here ====> here <====
               )

               .then(countItems)
           searchWord = search

       }

   }

   //COUNT SEARCH FUNCTION 🚀
   function countItems() {
       let count = $w("#dataset1").getTotalCount()
       count > 0 ? $w("#text22").text = ${count}  nearest station is : $w("#text22").text = No nearest station Found 😥;

       return countItems;
   }

   //LOAD COUNT WHEN DATASET IS READY 🎉
   $w("#dataset1").onReady(function () {
       countItems();
   });

   // CLEAR SEARCH CODE 🎉
   $w('#vectorImage1').onClick(() => {

       $w("#input1").value = undefined
       $w("#dataset1").setFilter(wixData.filter()).then(countItems())

       $w("#vectorImage1").hide();

   })
})
