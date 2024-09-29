**Binary Search**

``` C++
BinarySearch(A, i, j, key)
{
	if (i > j) then
		return -1
	
	k = floor(i+j/2)
	
	if (A[k] = key) then
		return k
		
	if (A[k] > key) then
		return BinarySearch(A, i, k-1, key)
	elseddeewcwòleoc *beiuc*
		return BinarySearch(A, k+1, j, key)
}

# Chiamata principale: BinarySearch(A, 0, n-1, key)
```

**Partition**

``` C++
Partition(A, p, r)
{
	x = A[r]
	i = p-1
	
	for (j = p to r-1) do
		if A[j] <= x then
		{
			i = i+1
			swap(A[i], A[j])
		}
	
	swap(A[i+1], A[r])
	return i+1
}
```

**Alberi**

``` C++
ContaNodi(T)
{
	if (T = NIL) then
		return 0
	return 1 + ContaNodi(t.left) + ContaNodi(t.right)
}

# Chiamata principale: ContaNodi(T)

Altezza(T)
{
	if (T = NIL) then
		return -1
	return 1 + max(Altezza(t.left), Altezza(t.right))
}

# Chiamata principale: Altezza(T)

DFS-PreOrder(T)
{
	if (T != NIL) then
	{
		# istruzioni - print t.val
		DFS-PreOrder(t.left)
		DFS-PreOrder(t.right)
	}
}

DFS-InOrder(T)
{
	if (T != NIL) then
	{
		DFS-InOrder(t.left)
		# istruzioni - print t.val
		DFS-InOrder(t.right)
	}
}

DFS-PostOrder(T)
{
	if (T != NIL) then
	{
		DFS-PostOrder(t.left)
		DFS-PostOrder(t.right)
		# istruzioni - print t.val
	}
}

BFS(T)
{
	if NOT (T = NIL) then
	{
		Q = new_queue()
		enqueue(Q, T)
	}
	
	while NOT (is_empty_queue(Q)) do
	{
		u = dequeue(Q)
		# analisi del nodo
		
		if (u.left != NIL) then
			enqueue(Q, u.left)
		if (u.right != NIL) then
			enqueue(Q, u.right)
	}
}
```

**Grafi**

``` C++
DFS(G)
{
	visited[1..n] new array
	prev[1..n] new array // array dei padri
	
	for all v on V do
	{
		visited[v] = FALSE
		prev[v] = 0
	}
	
	for all v on V do
		if (visited[v] = FALSE) then
			DFS-Visit(G, v)
	
	return prev[]
}

DFS-Visit(G, v)
{
	visited[v] = TRUE
	# analisi del nodo
	
	for all u, v on E do
		if visited[v] = FALSE then
		{
			prev[v] = u
			DFS-Visit(G, v)
		}
			
	# analisi del nodo post-visita
}

GraphConnected(G)
{
	visited[1..n] new array
	
	for all v on V do
		visited[v] = FALSE
		
	DFS-Visit(G, 1)
	
	for all v on V do
		if visited[v] = FALSE then
			return FALSE
			
	return TRUE
}

ComponentConnected(G)
{
	visited[1..n] new array
	CC = 0
	
	for all v on V do
		visited[v] = FALSE
		
	if visited[v] = FALSE then
	{
		CC = CC + 1
		DFS-Visit(G, v)
	}
	
	return CC
}

CC(G)
{
	cc[1..n] new array
	
	for all v on V do
		cc[v] = 0
	
	id = 0
	
	for all v on V do
		if cc[v] = 0 then
		{
			id = id + 1
			CC-Visit(G, v, id)
		}
	
	return cc
}

CC-Visit(G, v, id)
{
	cc[v] = id
	
	for all u, v on E do
		if cc[v] = 0 then
			CC-Visit(G, v, id)
}

DFS-Cycle-DirectGraph(G)
{
	pre[1..n] new array
	post[1..n] new array
	
	for all v on V do
	{
		pre[v] = 0
		post[v] = 0
		time = 0
	}
	
	for all v on V do
		if pre[v] = 0 then
			DFS-Visit(G, v)
}

DFS-Visit(G, v)
{
	time = time + 1
	pre[u] = time
	
	for all u, v on E do
	{
		if pre[v] = 0 then // tree
			DFS-Visit(G, v)
		
		if post[v] = 0 then // back
	}
	
	time = time + 1
	post[u] = time
}

BFS(G)
{
	dist[1..n] new array
	prev[1..n] new array
	
	for all v on V do
	{
		dist[v] = +inf
		prev[v] = 0
	}
	
	dist[s] = 0
	
	Q = new_queue()
	enqueue(Q, s)
	
	while NOT is_empty_queue(Q) do
	{
		u = dequeue(Q)
		# analisi nodo pre-visita
		for all u, v on E do
			if dist[v] = +inf then
			{
				enqueue(G, v)
				dist[v] = dist[u] + 1
				prev[v] = u
			}
	}
	
	return prev
}
```