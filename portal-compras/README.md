# 🛒 Portal de Solicitação de Compras

Sistema web para solicitação, acompanhamento e aprovação de pedidos de compra.

## 📁 Estrutura do projeto

```
portal-compras/
├── login.html               # Tela de login (local + Microsoft 365)
├── menu-inicial.html        # Dashboard principal
├── portal.html              # Formulário de nova solicitação
├── minhas-solicitacoes.html # Listagem e acompanhamento
├── relatorios.html          # Relatórios e gráficos
│
├── css/                     # Estilos separados por página
│   ├── login.css
│   ├── menu-inicial.css
│   ├── portal.css
│   ├── minhas-solicitacoes.css
│   └── relatorios.css
│
└── js/                      # Scripts separados por página
    ├── login.js
    ├── menu-inicial.js
    ├── portal.js
    ├── minhas-solicitacoes.js
    └── relatorios.js
```

## 🚀 Como usar

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/portal-compras.git
   ```

2. Abra o projeto no VS Code:
   ```bash
   cd portal-compras
   code .
   ```

3. Instale a extensão **Live Server** no VS Code (recomendado para desenvolvimento local).

4. Clique com o botão direito em `login.html` → **"Open with Live Server"**.

## 🔐 Configuração do Microsoft 365 (MSAL)

No arquivo `js/login.js`, localize e preencha:

```javascript
var MSAL_CLIENT_ID = 'SEU_CLIENT_ID_AQUI';   // Azure App Registration
var MSAL_TENANT_ID = 'SEU_TENANT_ID_AQUI';   // Tenant ID da sua organização
```

> Para obter essas credenciais: [portal.azure.com](https://portal.azure.com) → Azure Active Directory → Registros de aplicativo.

## 🔑 Login de demonstração

Para testar sem configurar o Microsoft 365:
- **E-mail:** qualquer e-mail válido (ex: `teste@empresa.com`)
- **Senha:** `123456`

> ⚠️ Substitua essa lógica por autenticação real em produção.

## 📦 Dependências externas (CDN)

| Biblioteca | Uso |
|---|---|
| [Nunito / Nunito Sans](https://fonts.google.com) | Tipografia |
| [Chart.js 4.4.1](https://cdnjs.cloudflare.com) | Gráficos nos relatórios |
| [SheetJS (xlsx) 0.18.5](https://cdnjs.cloudflare.com) | Exportação para Excel |
| [MSAL Browser 2.38.3](https://alcdn.msauth.net) | Autenticação Microsoft 365 |

## 🗺️ Navegação entre páginas

```
login.html
    └─→ menu-inicial.html
            ├─→ portal.html              (Nova Solicitação)
            ├─→ minhas-solicitacoes.html (Minhas Solicitações)
            └─→ relatorios.html          (Relatórios)
```

## 🛠️ Desenvolvimento

### Recomendações para VS Code

Extensões úteis:
- **Live Server** — servidor local com reload automático
- **Prettier** — formatação de código
- **HTML CSS Support** — autocompletar CSS em HTML

### Sessão de usuário

O sistema usa `sessionStorage` para manter o usuário logado:

```javascript
// Verificar autenticação em qualquer página
var user = JSON.parse(sessionStorage.getItem('portal_user') || 'null');
if (!user) window.location.href = 'login.html';

// Dados disponíveis
user.nome     // Nome completo
user.email    // E-mail
user.cargo    // Cargo (Microsoft Graph)
user.depto    // Departamento (Microsoft Graph)
user.provider // 'microsoft365' ou 'local'

// Logout
sessionStorage.removeItem('portal_user');
window.location.href = 'login.html';
```

## 📄 Licença

Uso interno. Todos os direitos reservados © 2026.
