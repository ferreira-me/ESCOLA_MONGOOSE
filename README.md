# 📚 Escola Mongoose

Este projeto é uma API desenvolvida em **Node.js** com **Express** e **MongoDB (Mongoose)** para gerenciar professores, disciplinas e suas associações. O objetivo é proporcionar uma base de CRUD com validações para CPF e e-mail, além de relacionamentos entre coleções.

## 🔧 Tecnologias Utilizadas

- Node.js
- Express
- MongoDB com Mongoose
- Validação de CPF e e-mail
- Testes com `curl`

---

## 📌 Endpoints Disponíveis

19
C:\Users\Maria Eduarda>curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Carlos Silva\", \"email\": \"carlos.silva@fatec.sp.gov.br\",  \"cpf\": \" 63479695051\"}"
{"nome":"Carlos Silva","email":"carlos.silva@fatec.sp.gov.br","cpf":"63479695051","_id":"6838ef11648459c40bc57d9a","__v":0}


C:\Users\Maria Eduarda>curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Odete Roitman\", \"email\": \"odete.roitman@fatec.sp.gov.br\",  \"cpf\": \" 32082128016\"}"
{"nome":"Odete Roitman","email":"odete.roitman@fatec.sp.gov.br","cpf":"32082128016","_id":"6838f130648459c40bc57da0","__v":0}


20

C:\Users\Maria Eduarda>curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Henrique Louro\", \"email\": \"henrique.louro@fatec.sp.gov.br\",  \"cpf\": \"07494812857\"}" Resposta: {"message":"CPF ou e-Mail já em uso"}

21

C:\Users\Maria Eduarda>curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Henrique Louro\", \"email\": \"henrique.louro@fatec.sp.gov.br\",  \"cpf\": \"12345678910\"}"
{"message":"12345678910 não é um CPF válido"}

22

C:\Users\Maria Eduarda>curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Henrique Louro\", \"email\": \"henrique.louro@fatec\",  \"cpf\": \"12345678910\"}"
{"message":"henrique.louro@fatec não é um formato de e-mail válido"}



23 
C:\Users\Maria Eduarda>curl -X GET http://localhost:3001/professor
[{"_id":"6838ed59ec0c2252e472c0c7","nome":"Henrique Louro","email":"henrique.louro@fatec.sp.gov.br","cpf":"07494812857","__v":0},{"_id":"6838ef11648459c40bc57d9a","nome":"Carlos Silva","email":"carlos.silva@fatec.sp.gov.br","cpf":"63479695051","__v":0},{"_id":"6838f130648459c40bc57da0","nome":"Odete Roitman","email":"odete.roitman@fatec.sp.gov.br","cpf":"32082128016","__v":0}]
C:\Users\Maria Eduarda>

24 
C:\Users\Maria Eduarda>curl -X PUT http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"id\":\"6838f130648459c40bc57da0\",\"nome\": \"Odetinha Roitman\", \"email\": \"odetinha.roitman@fatec.sp.gov.br\",  \"cpf\": \" 32082128016\"}"
{"_id":"6838f130648459c40bc57da0","nome":"Odetinha Roitman","email":"odetinha.roitman@fatec.sp.gov.br","cpf":"32082128016","__v":0}

25
C:\Users\Maria Eduarda>curl -X DELETE http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"id\":\"6838f130648459c40bc57da0\"}"
{"message":"Professor excluído com sucesso"}


26
C:\Users\Maria Eduarda> curl -X GET http://localhost:3001/professor
[{"_id":"6838ed59ec0c2252e472c0c7","nome":"Henrique Louro","email":"henrique.louro@fatec.sp.gov.br","cpf":"07494812857","__v":0},{"_id":"6838ef11648459c40bc57d9a","nome":"Carlos Silva","email":"carlos.silva@fatec.sp.gov.br","cpf":"63479695051","__v":0}]

27

C:\Users\Maria Eduarda>curl -X POST http://localhost:3001/disciplina -H "Content-Type: application/json" -d "{\"descricao\": \"Técnicas de Programação II\"}"
{"descricao":"Técnicas de Programação II","_id":"6838f35d648459c40bc57dac","__v":0}
C:\Users\Maria Eduarda>


C:\Users\Maria Eduarda>curl -X POST http://localhost:3001/disciplina -H "Content-Type: application/json" -d "{\"descricao\": \"Lógica de Programação\"}"
{"descricao":"Lógica de Programação","_id":"6838f383648459c40bc57dae","__v":0}

28
curl -X GET http://localhost:3001/disciplina
[{"_id":"6838f35d648459c40bc57dac","descricao":"Técnicas de Programação II","__v":0},{"_id":"6838f383648459c40bc57dae","descricao":"Lógica de Programação","__v":0}]


29
C:\Users\Maria Eduarda>curl -X POST http://localhost:3001/professor_has_disciplina -H "Content-Type: application/json" -d "{\"professor\": \"6838ef11648459c40bc57d9a\", \"disciplina\": \"6838f35d648459c40bc57dac\"}"
{"professor":"6838ef11648459c40bc57d9a","disciplina":"6838f35d648459c40bc57dac","_id":"6839028e648459c40bc57db7","__v":0}

30

C:\Users\Maria Eduarda>curl -X GET http://localhost:3001/professor_has_disciplina
[{"_id":"6839028e648459c40bc57db7","professor":{"_id":"6838ef11648459c40bc57d9a","nome":"Carlos Silva","email":"carlos.silva@fatec.sp.gov.br","cpf":"63479695051","__v":0},"disciplina":{"_id":"6838f35d648459c40bc57dac","descricao":"Técnicas de Programação II","__v":0}}]


## 🧪 Testado com:

- Postman
- `curl` via terminal (Windows)
