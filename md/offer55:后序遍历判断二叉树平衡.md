# 利用后续遍历判断二叉树是否是平衡二叉树
```cpp
int dfs(TreeNode* root){
    if(root==nullptr){
        return 0;
    }
    int left=dfs(root->left);
    if(left==-1){
        return -1;
    }
    int right=dfs(root->right);
    if(right==-1){
        return -1;
    }
    return abs(left-right)>1?-1:max(left,right)+1;
}
```
当返回值为-1时不是平衡二叉树，否则是平衡二叉树。