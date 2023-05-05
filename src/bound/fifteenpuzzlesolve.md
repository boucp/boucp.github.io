# 15 puzzle
## Algorithm
```cpp
#include <bits/stdc++.h>
#define MX 100005
#define N 4
using namespace std;

struct node
{
    node *parent;
    int pos[N][N], cost, x, y, level;
};
typedef node node;
node *a[MX];
int s = -1;
void min_heapify(int i, int n)
{
    int left = 2 * i + 1;
    int right = left + 1;
    int m = i;
    if (left < n && a[left]->cost + a[left]->level < a[m]->cost + a[m]->level)
        m = left;
    if (right < n && a[right]->cost + a[right]->level < a[m]->cost + a[m]->level)
        m = right;
    if (m != i)
    {
        swap(a[m], a[i]);
        min_heapify(m, n);
    }
}

int len(){
    return s;
}

void push(node *x)
{
    s++;
    int n = s;
    a[n] = x;
    while (n > 0 && a[n]->cost + a[n]->level < a[(n - 1) / 2]->cost + a[(n - 1) / 2]->level)
    {
        swap(a[n], a[(n - 1) / 2]);
        n = (n - 1) / 2;
    }
}
int isempty()
{
    return s == -1;
}
node *top()
{
    if (!isempty())
    {
        return a[0];
    }
    else
        return nullptr;
}

void pop()
{
    if (!isempty())
    {

        swap(a[0], a[s]);
        min_heapify(0, s);
        s--;
    }
    else
        cout << "que is empty\n";
}

node *createnode(int pos[N][N], node *parent, int x, int y, int tx, int ty, int l)
{
    node *child = new node;
    child->parent = parent;
    memcpy(child->pos, pos, sizeof(child->pos));
    swap(child->pos[x][y], child->pos[tx][ty]);
    child->x = tx;
    child->y = ty;
    child->cost = INT_MAX;
    child->level = l;
    return child;
}


int countcost(int arr[N][N], int ans[N][N])
{
    int count = 0;
    for (int i = 0; i < N; i++)
        for (int j = 0; j < N; j++)
        {
            if (arr[i][j] != ans[i][j])
                count++;
        }
    return count;
}
int col[4] = {1, -1, 0, 0};
int row[4] = {0, 0, 1, -1};
bool safezone(int x, int y)
{
    if (x >= 0 && x < N && y >= 0 && y < N)
        return true;
    return false;
}
void printpos(int arr[N][N])
{
    for (int i = 0; i < N; i++)
    {
        cout << "----------------\n";
        // cout<<"****************\n";
        {
            for (int j = 0; j < N; j++)
                printf("|%2d ", arr[i][j]);
        }

        cout << "|\n";
    }
    cout << "----------------\n\n";
}
void print(node *x)
{
    if (x != NULL)
    {
        print(x->parent);
        printpos(x->pos);
    }
}

bool solveable(int arr[N][N], int y, int z)
{

    int x = 0, a[N * N], k = -1;
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < N; j++)
        {
            a[++k] = arr[i][j];
            if (a[k] == 0)
                a[k] = N * N;
        }
    }
    int less = 0;
    if ((y + z) & 1)
        x = 1;
    for (int i = 0; i < N * N - 1; i++)
    {
        for (int j = i + 1; j < N * N; j++)
        {
            if (a[i] > a[j])
            {
                less++;
            }
        }
    }
    
    if ((less + x) & 1)
        return false;
    return true;
}

void LCsolve(int initial[N][N], int ans[N][N], int x, int y)
{
    int l = 0;
    node *root = createnode(initial, NULL, x, y, x, y, l);
    root->cost = countcost(root->pos, ans);
    push(root);
    while (!isempty())
    {
        node *enode = top();
        pop();
        if (enode->cost == 0)
        {
            print(enode);
            return;
        }
        else
        {
            for (int i = 0; i < 4; i++)
            {
                int u =enode->x + col[i];
                int v =enode->y + row[i];

                if (safezone(u, v))
                {
                    node *live = createnode(enode->pos, enode, enode->x, enode->y, u, v, l + 1);
                    live->cost = countcost(live->pos, ans);
                    
                    if(s==MX-1){
                        cout<<"NOT POSSIBLE TO SOLVED BY B&B ALGORITHM BECAUSE OF EXTREME SPACE MEMEORY.\nINSTEAD, TRY A* ALGORITHM FOR THIS TYPE OF COMPLEX PROBLEMS\n";
                        return;
                    }
                    push(live);
                }
            }
        }
    }
}

int main()
{
    // Use terminal, delete below two lines.
    freopen("input.txt", "r", stdin);
    freopen("output.txt", "w", stdout);
    int puzzle[N][N], answer[N][N], y, z;
    cout << "INITIAL STATE OF PUZZLE:\n";
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < N; j++)
        {
            cin >> puzzle[i][j];
            if (puzzle[i][j] == 0)
            {
                y = i;
                z = j;
            }
        }
    }
    printpos(puzzle);
    cout << "GOAL STATE OF PUZZLE:\n";
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < N; j++)
        {
            cin >> answer[i][j];
        }
    }
    printpos(answer);
    
    if (!solveable(puzzle, y, z))
    {
        cout << "THIS PUZZLE IS NOT SOLVEABLE.";
    }
    else{
        cout<<"THIS PUZZLE IS SOLVEABLE AND HERE IS THE SOLUTION:\n";
        LCsolve(puzzle, answer, y, z);
    }

    return 0;
}
```