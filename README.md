Project Breakdown
Trie Data Structure:

A Trie is a tree-like data structure used to store a dynamic set of strings where each node represents a single character of a string.
Nodes: Each node in the Trie contains:
A dictionary (unordered_map) of children nodes, where each key is a character and the value is a pointer to another TrieNode.
A boolean flag is_end_of_word that indicates whether the current node marks the end of a valid word.
Inserting Words:

Function: void insert(string word)
Process:
Start at the root node.
For each character in the word:
Check if the character is already a child of the current node.
If not, create a new node for this character.
Move to the corresponding child node.
After processing all characters, mark the last node as the end of a word.
Searching for a Prefix:

Function: TrieNode* search_prefix(string prefix)
Process:
Start at the root node.
Traverse the Trie following the characters of the prefix.
If any character in the prefix is not found, return nullptr (indicating no words with that prefix).
If the prefix is found, return the node where the prefix ends.
Finding Words with a Given Prefix:

Function: vector<string> get_words_with_prefix(string prefix)
Process:
First, use search_prefix to find the node corresponding to the last character of the prefix.
Perform a Depth-First Search (DFS) starting from that node to collect all words that start with the prefix.
Append each word found to a list, which is then returned as the suggestion list.
Autocomplete System:

Class: AutocompleteSystem
Initialization:
The system initializes a Trie and inserts a predefined list of words into it.
Getting Suggestions:
The system allows the user to input a prefix and then returns all words in the Trie that start with that prefix by calling get_words_with_prefix.
How the Code Works Together:
Initialization:

A list of words (e.g., ["hello", "hell", "heaven", "heavy"]) is provided to the AutocompleteSystem.
These words are inserted into the Trie one by one, where each word is stored as a path of nodes corresponding to its characters.
Querying for Suggestions:

When the user types a prefix (e.g., "he"), the system searches the Trie for this prefix.
If the prefix exists, the system performs a DFS from the node where the prefix ends, collecting all words that continue from that node.
The words are returned as suggestions to the user.
Example Walkthrough:
Inserting "hello":

Start at the root node.
Insert nodes for 'h', 'e', 'l', 'l', and 'o'.
Mark the node for 'o' as the end of the word.
Querying with Prefix "he":

The system finds the node for 'e' in the path "he".
It then performs a DFS from 'e', finding the words "hell", "hello", "heaven", and "heavy".
These words are returned as suggestions.
Benefits of Using Trie:
Efficiency: Tries allow for fast insertion and prefix search, both of which are O(m) operations, where m is the length of the word or prefix.
Space Utilization: Although Tries can be memory-intensive due to the number of nodes, they offer a trade-off by providing fast lookups.
Potential Enhancements:
Adding Frequency-Based Suggestions: Modify the Trie to store the frequency of each word and prioritize more frequently used words in the suggestions.
Autocomplete for Phrases: Extend the Trie to handle multi-word phrases, allowing for more complex autocomplete suggestions.
