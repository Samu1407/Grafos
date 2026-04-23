# Grafos
# Projeto Neo4j - Futebol

## 📌 Problema
Analisar relações entre jogadores, clubes e países.

## 🧠 Por que grafo?
Porque conexões são mais importantes que os dados isolados.

## 🗺️ Modelo
(coloque a imagem que você fez)

## ⚙️ Como rodar
1. Abrir Neo4j
2. Rodar script.cypher

## 📊 Queries
MERGE (br:Country {name: "Brasil"})
MERGE (ar:Country {name: "Argentina"})
MERGE (uy:Country {name: "Uruguai"})
MERGE (py:Country {name: "Paraguai"})
MERGE (bo:Country {name: "Bolivia"})

MERGE (neymar:Player {name: "Neymar"})
MERGE (miguel:Player {name: "Miguelito"})

MERGE (santos:Club {name: "Santos"})

MERGE (neymar)-[:PLAYS_FOR]->(santos)
MERGE (miguel)-[:PLAYS_FOR]->(santos)

MERGE (br)-[:PLAYED]->(ar)
MERGE (br)-[:PLAYED]->(uy)
MERGE (br)-[:PLAYED]->(py)
MERGE (br)-[:PLAYED]->(bo)

MERGE (neymar)-[:PLAYS_FOR_COUNTRY]->(br)
MERGE (miguel)-[:PLAYS_FOR_COUNTRY]->(bo)

-- Quais jogadores jogam no Santos?
MATCH (p:Player)-[:PLAYS_FOR]->(c:Club {name: "Santos"})
RETURN p

-- Quais países o Brasil já enfrentou?
MATCH (:Country {name: "Brasil"})-[:PLAYED]->(c)
RETURN c

-- Jogadores por país
MATCH (p:Player)-[:PLAYS_FOR_COUNTRY]->(c:Country)
RETURN c.name, collect(p.name)

## 🚧 Dificuldades
Ex: entender MERGE, modelagem, etc.
