Unique values of javascript array

```
letters = ["a", "b", "b", "c", "a", "c", "d"];
letters.filter(function(item, index, arr){return arr.indexOf(item) == index;});
["a", "b", "c", "d"]
```

Long version:

```
// .filter(callback) returns a new array with all elements for which the callback returns true

letters = ["a", "b", "b", "c", "a", "c", "d"];

var unique_letters = letters.filter(
function(item, index, original_array)
{
  var first_index_of_item_in_original_array = original_array.indexOf(item);
  if (index == first_index_of_item_in_original_array)
  {
    // the first occurrence of the item
    return true;
  }
  else
  {
    // either the item is not found (-1)
    // or it is not the first instance
    return false;
  }
});
```
