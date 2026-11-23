#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

struct Edge {
    int u, v, weight;
};

bool compare(Edge a, Edge b) {
    return a.weight < b.weight;
}

int findParent(vector<int>& parent, int x) {
    if (parent[x] == x)
        return x;
    return parent[x] = findParent(parent, parent[x]);
}

void unite(vector<int>& parent, int a, int b) {
    parent[findParent(parent, a)] = findParent(parent, b);
}

int main() {
    int V, E;
    cout << "Enter number of vertices and edges: ";
    cin >> V >> E;

    vector<Edge> edges(E);
    cout << "Enter source, destination and weight:\n";
    for (int i = 0; i < E; i++) {
        cin >> edges[i].u >> edges[i].v >> edges[i].weight;
    }

    sort(edges.begin(), edges.end(), compare);

    vector<int> parent(V);
    for (int i = 0; i < V; i++)
        parent[i] = i;

    int totalCost = 0, count = 0;
    cout << "Edges in Minimum Spanning Tree:\n";
    for (Edge e : edges) {
        int a = findParent(parent, e.u);
        int b = findParent(parent, e.v);

        if (a != b) {
            cout << e.u << " - " << e.v << ": " << e.weight << endl;
            totalCost += e.weight;
            unite(parent, a, b);
            count++;

            if (count == V - 1)
                break;
        }
    }

    if (count != V - 1) {
        cout << "Graph is disconnected. MST is not possible.\n";
    } else {
        cout << "Total cost of MST: " << totalCost << endl;
    }

    return 0;
}
