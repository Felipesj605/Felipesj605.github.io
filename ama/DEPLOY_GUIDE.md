# 🚀 Guia Rápido de Deploy - AMA Recicláveis

## ✅ O que você PRECISA fazer antes de fazer upload:

### 1. **Atualizar o Domínio** (OBRIGATÓRIO)
Antes de fazer upload, atualize o domínio real do site em:

**📄 `sitemap.xml`** - Linhas 10, 18, 25, 32, 39
- Substitua `https://www.amareciclaveis.com.br/` pelo seu domínio real
- Exemplo: `https://www.seudominio.com.br/`

**📄 `robots.txt`** - Linha 13
- Substitua `https://www.amareciclaveis.com.br/sitemap.xml` pelo seu domínio real
- Exemplo: `Sitemap: https://www.seudominio.com.br/sitemap.xml`

### 2. **Configurar HTTPS** (RECOMENDADO)
Quando você instalar o certificado SSL no servidor:

**📄 `.htaccess`** - Linha 7-8
- Descomente as linhas que forçam HTTPS:
```apache
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

### 3. **Verificar o Logo**
- ✅ Certifique-se de que `images/logo.png` está atualizado
- O favicon já está configurado para usar o logo

---

## 📤 Como Fazer Upload:

### Opção 1: FTP/SFTP
1. Conecte-se ao servidor via FTP
2. Faça upload de TODOS os arquivos e pastas:
   - `index.html`
   - `css/` (pasta completa)
   - `js/` (pasta completa)
   - `images/` (pasta completa)
   - `.htaccess`
   - `robots.txt`
   - `sitemap.xml`

### Opção 2: cPanel/File Manager
1. Acesse o File Manager do cPanel
2. Navegue até a pasta pública (geralmente `public_html` ou `www`)
3. Faça upload de todos os arquivos

### Opção 3: Git (se usar)
```bash
git add .
git commit -m "Deploy inicial"
git push origin main
```

---

## ⚙️ Configurações do Servidor:

### Permissões de Arquivos:
- **Arquivos**: 644 (rw-r--r--)
- **Pastas**: 755 (rwxr-xr-x)

### Estrutura de Pastas:
```
public_html/ (ou www/)
├── index.html
├── css/
├── js/
├── images/
├── .htaccess
├── robots.txt
└── sitemap.xml
```

---

## ✅ Checklist Rápido:

- [ ] Atualizar domínio no `sitemap.xml`
- [ ] Atualizar domínio no `robots.txt`
- [ ] Verificar se `images/logo.png` está atualizado
- [ ] Fazer upload de todos os arquivos
- [ ] Verificar permissões (644 para arquivos, 755 para pastas)
- [ ] Testar o site no navegador
- [ ] Instalar certificado SSL (se ainda não tiver)
- [ ] Descomentar regras HTTPS no `.htaccess` (após SSL)
- [ ] Testar links do WhatsApp
- [ ] Testar em mobile

---

## 🔍 Após o Deploy:

### 1. **Google Search Console**
- Acesse: https://search.google.com/search-console
- Adicione seu site
- Envie o `sitemap.xml`

### 2. **Testar o Site**
- Abra o site no navegador
- Teste todos os links
- Teste o menu mobile
- Teste o botão do WhatsApp
- Verifique se o mapa está funcionando

### 3. **Opcional - Google Analytics**
Se quiser rastrear visitantes, adicione o código do Google Analytics antes do `</head>` no `index.html`

---

## 🆘 Problemas Comuns:

### Logo não aparece?
- Verifique se o arquivo está em `images/logo.png`
- Faça hard refresh: `Ctrl + F5`

### Mapa não carrega?
- Verifique se o iframe do Google Maps está correto
- Pode precisar de uma API key do Google Maps (geralmente não é necessário)

### CSS não atualiza?
- Limpe o cache do navegador
- Verifique se a versão do CSS está atualizada no HTML

### HTTPS não funciona?
- Certifique-se de que o certificado SSL está instalado
- Descomente as regras no `.htaccess`

---

## 📞 Suporte

Se precisar de ajuda, verifique:
- `README.md` - Documentação completa
- `CHECKLIST.md` - Checklist detalhado

---

**Boa sorte com o deploy! 🚀**

