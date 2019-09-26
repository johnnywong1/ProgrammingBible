# Implement Trie (Prefix Tree)
Draft Java solution:
``` 
public class TrieNode {
    Character c;
    HashMap<Character, TrieNode> children;
    boolean isLeaf;

    public TrieNode(char c){
        this.c = c;
    }

    public TrieNode(){

    }
}

public class Trie {

    TrieNode root;

    public Trie(){
        this.root = new TrieNode();
    }

    /** Inserts a word into the trie. */
    public void insert(String word) {
        HashMap<Character, TrieNode> children = this.root.children;
        int cnt = 0;
        for(Character c : word.toCharArray()){
            TrieNode temp;
            if(children.containsKey(c)){
                temp = children.get(c);
            }else{
                temp = new TrieNode(c);
                //add new child
                children.put(c, temp);
            }
            children = temp.children;
            ++ cnt;
            if(cnt == word.length() - 1){
                temp.isLeaf = true;
            }
        }
    }

    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        //iterative search
        TrieNode temp = searchNode(word);
        return temp != null && temp.isLeaf;
    }

    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
        return searchNode(prefix) != null;  //no need to check isLeaf
    }

    private TrieNode searchNode(String word){
        HashMap<Character, TrieNode> children = this.root.children;
        TrieNode curr = null;
        for(Character c : word.toCharArray()){
            if(children.containsKey(c)){
                //go to next level
                curr = children.get(c);
                children = curr.children;
            }else{
                return null;
            }
        }
        return curr;    //last char node for word if root-to-leaf path found in tree
    }
}
```
Optimizations: use TrieNode[] as smaller lookup structure