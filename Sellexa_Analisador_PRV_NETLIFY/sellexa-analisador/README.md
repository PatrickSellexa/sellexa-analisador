# Analisador PRV — Sellexa

## Como publicar no Netlify (5 minutos)

### 1. Criar conta gratuita
Acesse https://netlify.com e crie uma conta gratuita.

### 2. Subir os arquivos
No painel do Netlify, clique em **"Add new site" → "Deploy manually"**.
Arraste a pasta `sellexa-analisador` inteira para a área de upload.

### 3. Configurar a chave da API (OBRIGATÓRIO)
No painel do site criado:
- Vá em **Site configuration → Environment variables**
- Clique em **"Add a variable"**
- Nome: `ANTHROPIC_API_KEY`
- Valor: sua chave da API da Anthropic (começa com `sk-ant-...`)
- Clique em **Save**

### 4. Fazer redeploy
Após salvar a variável, vá em **Deploys → Trigger deploy → Deploy site**.

### 5. Pronto!
O site estará disponível em um endereço como `sellexa-prv.netlify.app`.
Você pode configurar um domínio próprio em **Domain management**.

---

## Estrutura do projeto

```
sellexa-analisador/
├── public/
│   └── index.html          ← O app completo (frontend)
├── netlify/
│   └── functions/
│       └── analisar.js     ← Proxy seguro para a API (backend)
├── netlify.toml            ← Configuração do Netlify
└── README.md               ← Este arquivo
```

## Como funciona a segurança

A chave da API fica **somente no servidor** (variável de ambiente do Netlify).
O usuário nunca tem acesso à chave. As chamadas passam pelo proxy `/api/analisar`.

## Domínio personalizado

Para usar `analisador.gruposellexa.com`:
1. No Netlify: Domain management → Add custom domain
2. No seu DNS: adicione um CNAME apontando para o endereço do Netlify
3. O Netlify configura HTTPS automaticamente (gratuito)
