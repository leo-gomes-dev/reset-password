# 🔐 Password Reset Interface

![GitHub Pages](https://shields.io)
![Tech](https://shields.io)

Uma interface de usuário limpa, segura e responsiva para fluxos de redefinição de senha. O projeto foi estruturado para ser facilmente acoplado a qualquer API de autenticação backend (Node.js, Python, PHP, etc.), exigindo apenas a alteração do endpoint de destino.

---

## ✨ Funcionalidades

- **🔒 Validação de Token:** Captura automática do token de recuperação via parâmetros de URL (`?token=seu_token`).
- **🛡️ Segurança Preventiva:** Bloqueio de submissão caso o token não seja identificado e validação de igualdade entre as senhas inseridas.
- **⚡ UX Fluida:** Feedback visual em tempo real (estados de *Loading*, sucesso e tratamento de erros vindos da API).
- **🎨 Design Moderno:** Visual minimalista construído com CSS puro, totalmente responsivo e adaptável a dispositivos móveis.

---

## 🛠️ Como Configurar o Backend

Para integrar a tela com a sua própria API, você só precisa alterar a URL do método `fetch` dentro do arquivo principal.

1. Abra o arquivo `index.html` (ou seu arquivo de script correspondente).
2. Localize a linha do `fetch` dentro do evento de *submit*:
   ```javascript
   const response = await fetch("http://localhost:3000/auth/reset", { // 👈 Altere esta URL
     method: "POST",
     headers: { "Content-Type": "application/json" },
     body: JSON.stringify({ password, token }),
   });
   ```
3. Substitua `http://localhost:3000/auth/reset` pela URL pública ou local do seu servidor backend (ex: `https://seudominio.com`).

> **Nota de Integração:** O backend deve estar preparado para receber uma requisição **POST** com um JSON contendo as chaves `{ "password": "...", "token": "..." }` e retornar um status `200` em caso de sucesso.

---

## 🎮 Como Rodar Localmente

1. Clone o repositório em sua máquina:
   ```bash
   git clone https://github.com
   ```
2. Acesse a pasta do projeto.
3. Para testar o comportamento de validação, abra o arquivo `index.html` no navegador passando um token fictício na URL:
   ```text
   http://localhost:5500/index.html?token=123456
   ```

---

## 📦 Estrutura Esperada do Token

A aplicação espera que o link enviado ao e-mail do usuário final siga a seguinte estrutura de parâmetros para que a validação funcione corretamente:

```text
https://github.io
```
