# learn

Este repositório contém o site publicado em [eziquel.com](https://eziquel.com) utilizando GitHub Pages.

## 🚀 Como o Site é Publicado

O site é automaticamente publicado através do GitHub Actions sempre que há um push para a branch `main`. O workflow de deploy está configurado em `.github/workflows/deploy.yml` e realiza os seguintes passos:

1. Faz checkout do código
2. Configura o GitHub Pages
3. Faz upload dos arquivos estáticos
4. Realiza o deploy para GitHub Pages

O workflow pode ser executado manualmente através da aba "Actions" no GitHub (opção `workflow_dispatch`).

## 🌐 Configuração DNS Necessária

Para que o domínio `eziquel.com` aponte para este site, é necessário configurar os registros DNS no provedor de domínio (Registro.br, GoDaddy, Cloudflare, etc.).

### Opção 1: Registros A (Recomendado)

Adicione os seguintes registros A no seu provedor DNS:

```
Tipo: A
Nome: @ (ou deixe em branco)
Valor: 185.199.108.153

Tipo: A
Nome: @ (ou deixe em branco)
Valor: 185.199.109.153

Tipo: A
Nome: @ (ou deixe em branco)
Valor: 185.199.110.153

Tipo: A
Nome: @ (ou deixe em branco)
Valor: 185.199.111.153
```

### Opção 2: Registro CNAME

Alternativamente, você pode usar um registro CNAME:

```
Tipo: CNAME
Nome: www (ou @ se o provedor permitir)
Valor: eziquel.github.io
```

**Nota:** Para o domínio raiz (apex domain como `eziquel.com`), a maioria dos provedores requer registros A ao invés de CNAME.

## ✅ Como Verificar se o Site Está Ativo

1. **Verifique o GitHub Pages:**
   - Vá para Settings > Pages no repositório do GitHub
   - Confirme que o site está sendo publicado a partir da branch correta
   - Verifique se o domínio customizado está configurado corretamente

2. **Verifique a propagação DNS:**
   - Use ferramentas como [DNS Checker](https://dnschecker.org) ou [WhatsMyDNS](https://whatsmydns.net)
   - Digite `eziquel.com` e verifique se os IPs do GitHub Pages aparecem

3. **Teste o acesso:**
   - Abra o navegador e acesse [https://eziquel.com](https://eziquel.com)
   - O certificado SSL pode levar alguns minutos para ser provisionado

4. **Verifique o workflow:**
   - Vá para a aba "Actions" no GitHub
   - Confirme que o último workflow de deploy foi executado com sucesso

## 🔒 Certificado SSL

O GitHub Pages provisiona automaticamente um certificado SSL gratuito para domínios customizados após a configuração DNS estar correta. Este processo pode levar alguns minutos após a primeira configuração.

## ⏱️ Tempo de Propagação

- **Configuração GitHub Pages:** Instantânea
- **Propagação DNS:** Pode levar de alguns minutos até 24-48 horas
- **Provisionamento SSL:** 5-15 minutos após DNS estar configurado

## 📝 Estrutura do Projeto

```
.
├── .github/
│   └── workflows/
│       └── deploy.yml      # Workflow de deploy automático
├── index.html              # Página principal do site
├── CNAME                   # Configuração do domínio customizado
└── README.md              # Este arquivo
```

## 🛠️ Desenvolvimento Local

Para visualizar o site localmente:

```bash
# Opção 1: Python
python3 -m http.server 8000

# Opção 2: Node.js (npx)
npx http-server -p 8000

# Opção 3: PHP
php -S localhost:8000
```

Depois acesse `http://localhost:8000` no navegador.

## 📚 Recursos Adicionais

- [Documentação oficial do GitHub Pages](https://docs.github.com/pages)
- [Gerenciando domínio customizado](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [Solução de problemas com domínios customizados](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site/troubleshooting-custom-domains-and-github-pages)