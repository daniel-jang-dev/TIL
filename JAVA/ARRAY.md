## JAVA / Array, ArrayList

### 주요 methods
    add(E element)
    add(int index, E element)
    addAll(Collection<? extends E> c)
    addAll(int index, Collection<? extends E> c)
    clear()
    contains(Object o)
    get(int index)
    indexOf(Object o)
    lastIndexOf(Object o)
    isEmpty()
    remove(int index)
    remove(Object o)
    removeAll(Collection<?> c)
    removeRange(int fromIndex, int toIndex)
    set(int index, E element)
    size()
    subList(int fromIndex, int toIndex)
    toArray()

### How to sort an array
    int array[] = { 2, 5, -2, 6, -3, 8, 0, -7, -9, 4 };
    Arrays.sort(array);
    => -9, -7, -3, -2, 0, 2, 4, 5, 6, 8
### binary search
    int index = Arrays.binarySearch(array, 2);
    System.out.println("Found 2 @ " + index);
    => Found 2 @ 5 
### linear search
    int target = 0;
    for (int i = 0; i < array.length; i++) {
       if (array[i] == target) {
          System.out.println("Element found at index " + i);
          break;
       } 
    }
    => Element found at index 6 
### Bubble sort
    // 1. for loop in for loop
    static void bubbleSort(int[] a) {
      int n = a.length;
      int temp = 0;
      for(int i = 0; i < n; i++) {
       for(int j=1; j < (n-i); j++) {
        if(a[j-1] > a[j]) { 
           temp = a[j-1]; 
           a[j-1] = a[j];
           a[j] = temp;
        } 
       } 
      } 
    }
    
    // 2. while loop
    public void sortArray(int[] x) {
      boolean swapped = true;
      while (swapped) {
       swapped = false;
       for(int i=1; i<x.length; i++) {
         int temp=0;
         if(x[i-1] > x[i]) {
            temp = x[i-1];
            x[i-1] = x[i];
            x[i] = temp;
            swapped = true;
          }
        }
      }
    }
### How to reverse an array list ?
    Collections.reverse(list);
    
### How to reverse an array
    int[] numbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
    for (int i = 0; i < numbers.length / 2; i++) {
       int temp = numbers[i];
       numbers[i] = numbers[numbers.length - 1 - i];
       numbers[numbers.length - 1 - i] = temp;
    } 

### How to search the minimum and the maximum element in an array ?
    // 1. linear search
    int numbers[] = new int[]{8, 2, 7, 1, 4, 9, 5};
    int min = numbers[0];
    int max = numbers[0];
    for(int i = 1; i< numbers.length; i++) {
      if(numbers[i] > max)
        max = numbers[i];
      else if (numbers[i] < min)
        min = numbers[i];
    }
    // 2. Collections
    Integer[] numbers = { 8, 2, 7, 1, 4, 9, 5};
    int min = (int) Collections.min(Arrays.asList(numbers));
    int max = (int) Collections.max(Arrays.asList(numbers));
    
### How to merge two arrays ?
    String a[] = { "A", "E", "I" };
    String b[] = { "O", "U" };
    List list = new ArrayList(Arrays.asList(a));
    list.addAll(Arrays.asList(b));
    String[] arr = list.toArray(new String[list.size()]);
    
### How to fill (initialize at once) an array ?
    Array.fill(arrayname,value)
    Array.fill(arrayname, starting index, ending index, value)
    
### How to extend an array after initialisation?
    System.arraycopy(Object source, int sourcePosition, Object destination, int destinationPosition, int length)
    String[] names = new String[] { "A", "B", "C" };
    String[] extended = new String[5];
    extended[3] = "D";
    extended[4] = "E";
    System.arraycopy(names, 0, extended, 0, names.length);
    
### How to remove an element of ArrayList?
    list.remove(int index)
    list.remove(Object o)

### How to remove one ArrayList from another ArrayList?
    objArray.removeAll(objArray2);

### How to find an object or a string in an ArrayList?
    objArray.contains(Object o)
    objArray.contains(objArray2)

## How to check if two arrays are equal or not?
    Arrays.equals(array1, array2)
    arr1 == arr2

