**DEFINIZIONE**
Una collezione di sottoinsiemi disgiunti di un insieme generativo. Ammette operazioni di ricerca ed unione, ma non inserzione e cancellazione.

Ogni insieme è rappresentato da un albero, ogni insieme ha un rappresentante che è la radice dell'albero.

**PRIMITIVE**
1) Make-set(X): Restituisce un disjoint set.
2) Find-set(DS, x): Restituisce il rappresentante dell'insieme a cui appartiene.
3) Union(DS, x, y): Unisce gli insiemi a cui appartengono x ed y.

Costo computazionale: `O(n).`

``` C++
Make-Set(X)
{
	DS[1..n] new array;
	for (i = 1 to n) do
		DS[i] = i;
	
	return DS;
}

Find-Set(DS, x)
{
	if (DS[x] = x) then
		return x;
	else
		Find-Set(DS, DS[x]);
}

Union(DS, x, y)
{
	xr = Find-Set(DS, x);
	yr = Find-Set(DS, y);
	if (xr != yr) then
		DS[xr] = yr;	
}
```

**EURISTICA DEL RANGO**
Nella Union l'albero più basso diventa sottoalbero di quello più alto.
Usiamo un array `rank[1..n]` che memorizza l'altezza degli alberi radicati nei rappresentanti e un array `p[1..n]` che è il vettore dei padri.

Usando l'euristica del rango riusciamo ad ottimizzare il costo computazionale delle primitive Find e Union che arrivano a costare `O(log(n)).`

``` C++
Make-Set(X)
{
	DS.p = new_array[1..n];
	DS.rank = new_array[1..n];
	
	for (i = 1 to n) do
	{
		DS.p[i] = i;
		DS.rank[i] = 0;
	}
	
	return DS;
}

Find-Set(DS, x)
{
	if (DS.p[x] = x) then
		return x;
	else
		Find-Set(DS, DS.p[x]);
}

Union(DS, x, y)
{
	xr = Find-Set(DS, x);
	yr = Find-Set(DS, y);
	
	if (xr != yr) then
	{
		if (DS.rank[xr] > DS.rank[yr]) then
			DS.p[yr] = xr;
		else
			DS.p[xr] = yr;
			
			if(DS.rank[xr] = DS.rank[yr]) then
				DS.rank[yr] = DS.rank[yr] + 1;
	}
		
}
```
