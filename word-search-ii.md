# Word Search II
Draft Java solution:
```
    public List<String> findWords(char[][] board, String[] words) {
        //return all words present in board ref dictionary
        //DFS approach
        Set<String> result = new HashSet();
        for(String word : words){
            for(int i = 0; i < board.length; ++ i){
                for(int j = 0; j < board[0].length; ++ j){
                    if(board[i][j] == word.charAt(0) && isWordPresent(board, word, i, j)){
                        result.add(word);
                    }
                }
            }
        }
        return new ArrayList(result);
    }

    private boolean isWordPresent(char[][] board, String word, int i, int j){
        boolean[][] visited = new boolean[board.length][board[0].length];
        return DFS(visited, board, word, i, j);
    }

    private boolean DFS(boolean[][] visited, char[][] board, String word, int i, int j){
        //boundary conditions
        if(i < 0 || i >= board.length || j < 0 || j >= board[0].length || visited[i][j] || board[i][j] != word.charAt(0)){
            return false;
        }
        //return condition
        if(board[i][j] == word.charAt(0)){
            if(word.length() == 1){
                return true;
            }else{
                visited[i][j] = true;   //keep exploring
            }
        }
        boolean result = DFS(visited, board, word.substring(1), i + 1, j) || DFS(visited, board, word.substring(1), i - 1, j) ||
         DFS(visited, board, word.substring(1), i, j + 1) ||
         DFS(visited, board, word.substring(1), i, j - 1);
        
        visited[i][j] = result;
        return result;
    }
```
PASSED

More efficient approach (trie - path must exist in trie tree for word to be present):
```
class TrieNode{
        public Map<Character, TrieNode> children;
        public String word;
        public TrieNode(){
            this.children = new HashMap<>();
            this.word = null;
        }
    }
    class TrieTree{
        TrieNode root;
        public TrieTree(){
            root = new TrieNode();
        }
        public void insert(String word){
            TrieNode node = root;
            for(char c : word.toCharArray()){
                if(!node.children.containsKey(c)){
                    node.children.put(c, new TrieNode());
                }
                node = node.children.get(c);
            }
            node.word = word;
        }
    }
    public int m, n;
    public int[] dx = {-1, 1, 0, 0};
    public int[] dy = {0, 0, -1, 1};
    public List<String> findWords(char[][] board, String[] words) {
        List<String> list = new ArrayList<>();
        if(board == null || board.length == 0 || board[0].length == 0 || words == null || words.length == 0) return list;
        TrieTree tree = new TrieTree();
        for(String word : words){
            tree.insert(word);
        }
        m = board.length;
        n = board[0].length;
        boolean[][] visited = new boolean[m][n];
        Set<String> set = new HashSet<>();
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                dfs(set, board, visited, i, j, tree.root);
            }
        }
        list.addAll(set);
        return list;
    }
    public void dfs(Set<String> list, char[][] board, boolean[][] visited, int x, int y, TrieNode root){
        if(root.word != null){
            list.add(root.word);
        }
        
        if(x < 0 || x >= m || y < 0 || y >= n || visited[x][y] || !root.children.containsKey(board[x][y])) return;
        root = root.children.get(board[x][y]);
        for(int i = 0; i < 4; i++){
            int nx = x + dx[i];
            int ny = y + dy[i];
            visited[x][y] = true;
            dfs(list, board, visited, nx, ny, root);
            visited[x][y] = false;
        }
    }
```