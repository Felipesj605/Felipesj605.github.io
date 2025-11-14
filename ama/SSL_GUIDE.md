# 🔒 Guia Completo: Certificado SSL para AMA Recicláveis

## O que é SSL e por que você precisa?

SSL (Secure Sockets Layer) é um certificado que criptografa a conexão entre o navegador e o servidor, permitindo que seu site use **HTTPS** ao invés de **HTTP**. Isso é importante porque:

- ✅ Google prioriza sites com HTTPS no ranking
- ✅ Navegadores mostram "Não seguro" para sites sem HTTPS
- ✅ Protege dados dos visitantes
- ✅ Aumenta a confiança dos clientes

---

## 🆓 Opção 1: Certificado SSL Gratuito (Let's Encrypt) - RECOMENDADO

### Para quem tem cPanel/Hospedagem Compartilhada:

#### Passo 1: Acessar o cPanel
1. Faça login no cPanel da sua hospedagem
2. Procure por "SSL/TLS" ou "Let's Encrypt"

#### Passo 2: Instalar Let's Encrypt
1. Clique em "SSL/TLS Status" ou "Let's Encrypt"
2. Selecione seu domínio
3. Clique em "Run AutoSSL" ou "Install"
4. Aguarde alguns minutos
5. Pronto! O certificado será instalado automaticamente

#### Passo 3: Verificar
- Acesse seu site com `https://seudominio.com.br`
- Deve aparecer um cadeado verde no navegador

---

## 🆓 Opção 2: Cloudflare (Gratuito e Fácil)

### Vantagens:
- ✅ Totalmente gratuito
- ✅ SSL automático
- ✅ CDN (acelera o site)
- ✅ Proteção DDoS

### Como configurar:

#### Passo 1: Criar conta
1. Acesse: https://www.cloudflare.com
2. Crie uma conta gratuita
3. Adicione seu domínio

#### Passo 2: Configurar DNS
1. Cloudflare mostrará os nameservers
2. Vá até onde você comprou o domínio
3. Substitua os nameservers pelos do Cloudflare
4. Aguarde propagação (pode levar até 24h, geralmente 1-2h)

#### Passo 3: Ativar SSL
1. No painel do Cloudflare, vá em "SSL/TLS"
2. Selecione "Flexible" ou "Full"
3. Pronto! Seu site terá HTTPS automaticamente

---

## 💰 Opção 3: Certificado SSL Pago

### Quando usar:
- Se sua hospedagem não oferece Let's Encrypt
- Se você precisa de validação estendida (EV SSL)
- Se você precisa de garantia maior

### Onde comprar:
- **Namecheap**: ~$8/ano
- **GoDaddy**: ~$70/ano
- **DigiCert**: ~$200/ano (mais seguro)

### Como instalar (cPanel):
1. Compre o certificado
2. Receba os arquivos: `.crt`, `.key`, `.ca-bundle`
3. No cPanel, vá em "SSL/TLS"
4. Clique em "Install and Manage SSL for your site"
5. Cole os arquivos nos campos correspondentes
6. Clique em "Install Certificate"

---

## 🔧 Instalação Manual (VPS/Dedicated Server)

### Se você tem acesso root ao servidor:

#### Para Apache:
```bash
# 1. Instalar Certbot
sudo apt-get update
sudo apt-get install certbot python3-certbot-apache

# 2. Obter certificado
sudo certbot --apache -d seudominio.com.br -d www.seudominio.com.br

# 3. Renovação automática (já configurada)
sudo certbot renew --dry-run
```

#### Para Nginx:
```bash
# 1. Instalar Certbot
sudo apt-get update
sudo apt-get install certbot python3-certbot-nginx

# 2. Obter certificado
sudo certbot --nginx -d seudominio.com.br -d www.seudominio.com.br

# 3. Renovação automática
sudo certbot renew --dry-run
```

---

## ✅ Após Instalar o SSL

### 1. Atualizar o `.htaccess`

No arquivo `.htaccess`, descomente as linhas 7-8:

```apache
# Antes (comentado):
# RewriteCond %{HTTPS} off
# RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

# Depois (descomentado):
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

### 2. Testar o Site

1. Acesse: `https://seudominio.com.br`
2. Verifique se aparece o cadeado verde
3. Teste se o HTTP redireciona para HTTPS

### 3. Atualizar URLs no Site

Se você tiver URLs hardcoded no código, atualize para HTTPS:
- `sitemap.xml` - já deve estar com HTTPS
- `robots.txt` - já deve estar com HTTPS
- Qualquer link interno no HTML

---

## 🔄 Renovação Automática

### Let's Encrypt expira a cada 90 dias

**cPanel**: Geralmente renova automaticamente

**Cloudflare**: Renovação automática, sem ação necessária

**VPS/Server**: Certbot renova automaticamente se configurado corretamente

---

## 🆘 Problemas Comuns

### "Certificado não confiável"
- Aguarde alguns minutos após instalação
- Limpe o cache do navegador
- Verifique se o certificado está instalado corretamente

### "Site não redireciona para HTTPS"
- Verifique se descomentou as linhas no `.htaccess`
- Certifique-se de que o módulo `mod_rewrite` está ativo

### "Erro de certificado misto"
- Certifique-se de que todas as imagens/scripts usam HTTPS
- Verifique o console do navegador (F12) para erros

---

## 📋 Checklist Pós-Instalação

- [ ] Certificado SSL instalado
- [ ] Site acessível via HTTPS
- [ ] Cadeado verde aparece no navegador
- [ ] HTTP redireciona para HTTPS
- [ ] `.htaccess` atualizado
- [ ] `sitemap.xml` com URLs HTTPS
- [ ] `robots.txt` com URLs HTTPS
- [ ] Testado em diferentes navegadores

---

## 💡 Recomendação

**Para a maioria dos casos, use Let's Encrypt (gratuito) via cPanel ou Cloudflare.**

É gratuito, fácil de instalar e funciona perfeitamente para sites comerciais.

---

## 📞 Precisa de Ajuda?

Se sua hospedagem oferece suporte:
- Entre em contato com o suporte técnico
- Peça para instalar Let's Encrypt
- Eles geralmente fazem isso em minutos

---

**Boa sorte! 🔒**

