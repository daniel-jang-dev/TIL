## JAVA / String

### Methods
    char charAt(int index)
    String substring(int beginIndex)
    String substring(int beginIndex, int endIndex)
    char[] toCharArray()
    boolean startsWith(String prefix)
    boolean endsWith(String suffix)
    int indexOf(int c)
    int indexOf(int c, int fromIndex)
    int indexOf(String str)
    int indexOf(String str, int fromIndex)
    int lastIndexOf(int c)
    String replace(char oldChar, char newChar)
    String replaceAll(String regex, String replacement)
    String[] split(String regex)
    String toLowerCase()
    String toUpperCase()
    String trim()

### How to change char array to String
    new String(charArray)

### How to change char to String?
    Character.toString(char c)
    String.valueOf(char c)

### How to compare two strings ?
    string1.comareTo(String string2)
    string1.compareToIgnoreCase((String string2)
    string1.compareTo(Object object) 
    : returns the ascii difference of first odd characters of compared strings.
    
    string1.equals(String string2) 
    : true / false

### How to remove a particular character from a string ?
    public static String removeCharAt(String s, int pos) {
      return s.substring(0, pos) + s.substring(pos + 1);
    }
    
### How to replace a substring inside a string by another one ?
    string.replace("A", "B");

### How to reverse a String?
    String string = "abcdef";
    
    // 1. StringBuffer
    String reverse = new StringBuffer(string).reverse().toString();
    
    // 2. String -> char array -> reverse -> String 
    char[] array = string.toCharArray();
    List<Character> list = new LinkedList<>();
    for(char c: array)
      list.add(c);
    Collections.reverse(list);
    String reverse = Stream.of(list).map(c -> new String(c)).collect(Collectors.joining());
    
### How to search a word inside a string ?
    string.indexOf(String word) 
    : returns a position index of a word within the string if found. Otherwise it returns -1.
    
### How to convert a string totally into upper case
    string.toUpperCase()
