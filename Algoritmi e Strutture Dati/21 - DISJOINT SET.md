**DISJOINT SET**
Un Disjoint Set è una struttura dati che memorizza una collezione di sottoinsiemi di nodi disgiunti, uniti tra di loro da un insieme. Ammette operazioni di unione, ricerca ma non inserzione e cancellazione.

**PRIMITIVE**
- **Make-set(X)**: Ritorna un Disjoint Set.
- **Find-set(DS, x)**: Restituisce un rappresentante del Disjoint Set.
- **Union(DS, x, y)**: Unisce due nodi in un unico insieme.

``` C++
Make-Set(X)
{
	DS = new array[1..n]
	for i = 1 to n do
		DS[i] = i
	return DS
}

// O(n)

Find-Set(DS, x)
{
	if DS[x] = x
		then return x
		else return Find-Set(DS, DS[x])
}

// O(n)

Union(DS, x, y)
{
	xr = Find-Set(DS, x)
	yr = Find-Set(DS, y)
		if xr != yr then
			DS[xr] = yr
}

// O(n)
```