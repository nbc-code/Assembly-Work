Members:
Ryan Banks, rmbanks
Noah Cantrell, nbc

In main, it first builds the array by branching to array_builder then it branches to the selection_sort procedure to sort the array.

In array_builder it first sets the starting address of the array into X0 then the size of the array in X1. It then adds 16, 8, 4, 2, and 1
into the array in reverse order.

In selection_sort it first checks array bounds, X4 is set to be the beginning of the array and X1, the end of it. If the array is at the end, the program is then 
complete and the array is sorted so it branches to the end procedure to print final values and halt (which also dumps). During the body of the procedure, the LR
is stored and calls find_smallest. Once that is complete, we restore the LR and continue onto swap. Here, we once again store the LR and call the swap procedure. Once
that is finished, the LR is restored and one iteration has been complete so the index, held with X4 is incremented and we loop back to the top of the selection_sort procedure

In swap it add, shifts, and loads the registers of note in our array X4 and X5 
(containing the index of the smallest value as well as the index of the value the smallest is to swap with)
into temporary registers X2 and X3. From here we store those into temporary registers X9 and X13.

In find_smallest it first stores the LR and all of the temporaries so it doesn't overwrite the values used in selection_sort then
initializes X9, X10, X11, X12 to the smallest index, smallest address, smallest value, and the current index. It then loops through checking if 
the current index is within bounds of the array and checks all of the values in the array against the smallest value. If the current value is 
less than the smallest value then the smallest index, smallest address, and smallest value are all set to the current index, current address, and
current value. It also sets the return value, X5, which is the new index of the smallest value in the array. When it gets to the end of the loop
it restores the temporaries and the LR then branches back to selection_sort with X5 being the smallest index in the array.