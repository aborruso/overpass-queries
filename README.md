# overpass-queries
Repositories for overpass-turbo and overpass-api queries


## Ricette

### Tutti i parcheggi presenti nell'area attiva
- **Cuoco**: [Christian Cantoro](https://wiki.openstreetmap.org/wiki/User:CristianCantoro)
- **Query live**: [http://overpass-turbo.eu/s/gyx](http://overpass-turbo.eu/s/gyx)
- **Difficoltà**: bassa

Con questa query per Overpass turbo è possibile avere restituito tutti i parcheggi:

- sia nodi, che aree;
- senza pagamento di pedaggio;
- senza cancelli all'ingresso;
- con accesso libero.

#### Codice

```XML
<query type="node">
  <has-kv k="amenity" v="parking"/>
  <has-kv k="fee" modv="not" v="yes"/>
  <has-kv k="access" modv="not" v="private"/>
  <has-kv k="barrier" modv="not" v="gate"/>
  <bbox-query {{bbox}}/>
</query>
<print/>
<query type="way">
	<has-kv k="amenity" v="parking"/>
    <has-kv k="fee" modv="not" v="yes"/>
  	<has-kv k="access" modv="not" v="private"/>
  	<has-kv k="barrier" modv="not" v="gate"/>
	<bbox-query {{bbox}}/>
</query>
<union>
  <item/>
  <recurse type="down"/>
</union>
<print/>
```


