Merkle Tree可以看做Hash List的泛化（Hash List可以看作一种特殊的Merkle Tree，即树高为2的多叉Merkle Tree）。

在最底层，和Hash List一样，把数据分成小的数据块，计算对应的哈希值。但之后并非直接去运算根哈希，而是把相邻的两个哈希合并成一个字符串，然后计算这个新字符串的哈希值，以此类推，最终形成一棵倒挂的树。倘若该层节点不足以两两分完，则将最后一个节点记录下来，并以它为头节点对应的树上的所有节点高度均加一作为下一层节点进行，以符合RFC6962要求。
new_node为用于创建新节点的宏函数；

void print_tree(merkletree* tree, int height)用于打印出生成的Merkletree；

uint hash(char* s1, char* s2)用于计算单个节点的哈希值；

uint hash_nodes(uint n1, uint n2)用于计算由两个旧节点生成的新节点的哈希值；

merkletree* last_node(merkletree* tree)用于寻找当前merkletree中最后一个节点；

merkletree* find_new_node(merkletree* tree)用于寻找可插入的新节点；

merkletree* initial(merkletree* tree, char** s, int n)生成merkletree，倘若该层节点不足以两两分完，则将最后一个节点记录下来，并以它为头节点对应的树上的所有节点高度均加一作为下一层节点进行，以符合RFC6962要求。

void delete_tree(merkletree* tree)删除merkletree；

char** divide_string(char* str, int* number)merkletree支持字符串的存储，且以标点符号为分割；

void delete_string(char** s, int n)删除字符串；
![image](https://github.com/TraceAJ/project5/assets/110471272/dfab1858-147e-4cbd-8568-0292493232e3)
