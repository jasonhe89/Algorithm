```python
class Solution:
    # @param strs: a list of strings
    # @return: A list of string
    def anagrams(self, strs):
        dict = {}
        for word in strs:
            sortedword = ''.join(sorted(word))
            dict[sortedword] = [word] if sortedword not in dict else dict[sortedword] + [word]
        result = []
        for item in dict:
            if len(dict[item]) >= 2:
                result += dict[item]
        return result
```

```python
class Anagram:
    # @param {str} line a text, for example "Bye bye see you nex"
    def mapper(self, _, line):
        for word in line.split():
            yield ''.join(sorted(list(word))), word
    
    def reducer(self, key, values):
        yield key, list(values)
```

/\*\* \* Definition of OutputCollector: \* class OutputCollector\<K, V\> { \* public void collect(K key, V value); \* // Adds a key/value pair to the output buffer \* } \*/ public class Anagram { public static class Map { public void map(String key, String value, OutputCollector\<String, String\> output) { // Write your code here // Output the results into output buffer. // Ps. output.collect(String key, String value); StringTokenizer tokenizer = new StringTokenizer(value); while (tokenizer.hasMoreTokens()) { String word = tokenizer.nextToken(); String original = word; char[] chars = original.toCharArray(); Arrays.sort(chars); String sorted = new String(chars); output.collect(sorted, word); } } } public static class Reduce { public void reduce(String key, Iterator\<String\> values, OutputCollector\<String, List\<String\>\> output) { // Write your code here // Output the results into output buffer. // Ps. output.collect(String key, List\<String\> value); List\<String\> results = new ArrayList\<String\>(); while (values.hasNext()) { results.add(values.next()); } output.collect(key, results); } } }

