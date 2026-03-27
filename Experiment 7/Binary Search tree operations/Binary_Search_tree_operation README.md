/*#include <stdio.h>
                
                inorderTraversal(root);
                printf("\n");
                break;

            
            case 3:
               
                preorderTraversal(root);
                printf("\n");
                break;

            
            case 4:
                
                postorderTraversal(root);
                printf("\n");
                break;

            
            case 5: {
                
                printf("Delete: ");
                scanf("%d", &data);
                int found = 0;
                root = deleteNode(root, data, &found);
                if (!found) {
                    printf("Value not found\n");
                }
                break;
            }

            case 6:
                freeTree(root);
                exit(0);

            default:
                
                printf("Invalid choice\n");
        }
    }

    return 0;
}*/ #include <stdio.h>
#include <stdlib.h>

struct TreeNode {
    int val;
    struct TreeNode* left;
    struct TreeNode* right;
};

// Insert node (duplicates go to right)
struct TreeNode* insertNode(struct TreeNode* root, int data) {
    if (root == NULL) {
        struct TreeNode* newNode = (struct TreeNode*)malloc(sizeof(struct TreeNode));
        newNode->val = data;
        newNode->left = newNode->right = NULL;
        return newNode;
    }

    if (data < root->val)
        root->left = insertNode(root->left, data);
    else
        root->right = insertNode(root->right, data);

    return root;
}

// Inorder Traversal
void inorderTraversal(struct TreeNode* root) {
    if (root == NULL)
        return;
    inorderTraversal(root->left);
    printf("%d ", root->val);
    inorderTraversal(root->right);
}

// Preorder Traversal
void preorderTraversal(struct TreeNode* root) {
    if (root == NULL)
        return;
    printf("%d ", root->val);
    preorderTraversal(root->left);
    preorderTraversal(root->right);
}

// Postorder Traversal
void postorderTraversal(struct TreeNode* root) {
    if (root == NULL)
        return;
    postorderTraversal(root->left);
    postorderTraversal(root->right);
    printf("%d ", root->val);
}

// Find minimum value node (used in delete)
struct TreeNode* findMin(struct TreeNode* root) {
    while (root->left != NULL)
        root = root->left;
    return root;
}

// Delete node
struct TreeNode* deleteNode(struct TreeNode* root, int key, int* found) {
    if (root == NULL)
        return NULL;

    if (key < root->val) {
        root->left = deleteNode(root->left, key, found);
}
