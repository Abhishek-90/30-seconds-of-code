Array: <table>
    <tr>
        <td>2</td>
        <td>4</td>
        <td>5</td>
        <td>1</td>
        <td>3</td>
        <td>0</td>
    </tr>
</table>

<p>
Above Array needs to be sorted, common algorithms that come to mind are Bubble sort, Insertion sort, Selection sort. These give O(n^2) Time Complexity. But if Looked closely, above array is not a random array, all the elements inside these Array belongs to the range [0,n-1], where n is size of array and every element in this range is present. 

Such special Arrays can be sorted using Cyclic Sort. 

Intution behind Cyclic sort, if the elements in an array belong to range [0,n-1], the ith element in this range should be placed at ith position in the Array to sort the array.

Example: 
Sorted sequence of above array looks like: 

Array: <table>
    <tr>
        <td>0</td>
        <td>1</td>
        <td>2</td>
        <td>3</td>
        <td>4</td>
        <td>5</td>
    </tr>
</table>

Notice, element at ith position in the array is i itself.

Code: 

</p>

let array = new Array(2,4,5,1,3,0);

let start = 0;

while(start < array.length){
    if(array[start] === start){
        start++; //if (element at position i) == i, the element is at its rightful position, so simply increment it.
    }
    else{
        //if (element at i) !== i, put the element at i, at arr[arr[i]]
        //say, element at index postion 0 is 2, swap arr[0] (i.e 2) with arr[arr[0]]
        //it makes arr[2] = 2(condition for sorted sequence) and arr[0] will be equal to arr[2](before swapping)

        let temp = arr[start];
        arr[start = arr[arr[start]]];
        arr[arr[start]] = temp;

        //don't increment start yet, as swap at position start might not have set arr[start] to right value. 
    }
}


<p>
    Time Complexity for Cyclic sort is O(n) where n is size of array.
</p>