# 🚀 Phoenix N8N Workflows

Workflows n8n pour l'écosystème Phoenix - Orchestrateur central pour microservices.

## 📋 **Vue d'ensemble**

Ce dépôt contient tous les workflows n8n qui coordonnent l'écosystème Phoenix :
- **Phoenix Letters** (Génération de lettres IA)
- **Phoenix CV** (Génération de CV optimisés)
- **Phoenix Website** (Site vitrine & SSO)

## 📁 **Structure du dépôt**

```
phoenix-n8n-workflows/
├── 📄 .env.example                              # Variables d'environnement
├── 📄 README.md                                 # Ce fichier
├── 📁 docs/                                     # Documentation
│   ├── PHOENIX_N8N_GUIDE.md                   # Guide d'installation
│   ├── PHOENIX_SSO_GUIDE.md                   # Guide SSO
│   └── PHOENIX_WORKFLOWS_AUDIT.md             # Audit des workflows
└── 🔄 Workflows JSON
    ├── phoenix-ecosystem-master-final.json     # 🎛️ Orchestrateur principal
    ├── phoenix-stripe-checkout-creator.json    # 💳 Paiements Stripe
    ├── phoenix-stripe-subscription-manager.json # 💰 Gestion abonnements
    ├── phoenix-stripe-webhooks-complete.json   # 🔔 Webhooks Stripe
    ├── phoenix-ecosystem-sso-integrated.json   # 🔐 SSO cross-apps
    ├── phoenix-letters-generator.json          # ✍️ Génération lettres
    ├── phoenix-cv-generator.json               # 📄 Génération CV
    ├── phoenix-signup-workflow.json            # 👤 Inscription utilisateurs
    ├── phoenix-health-check-workflow.json      # 🩺 Monitoring santé
    └── phoenix-quota-check-workflow.json       # 📊 Gestion quotas
```

## ⚡ **Installation rapide**

### 1. **Cloner le dépôt**
```bash
git clone https://github.com/Alvarezitooo/phoenix_n8n.git
cd phoenix_n8n
```

### 2. **Configurer les variables**
```bash
# Copier le template
cp .env.example .env

# Éditer avec vos valeurs
nano .env
```

### 3. **Importer dans n8n**
1. Ouvrir votre instance n8n
2. Aller dans **Workflows** > **Import from file**
3. Importer chaque fichier JSON
4. Configurer les credentials dans **Settings** > **Credentials**

## 🔧 **Configuration requise**

### **Variables d'environnement**
Configurez ces variables dans n8n **Settings** > **Environment Variables** :

```bash
# URLs des microservices
PHOENIX_LETTERS_URL=https://phoenix-letters.cloudrun.app
PHOENIX_CV_URL=https://phoenix-cv.cloudrun.app
PHOENIX_WEBSITE_URL=https://phoenix-website.vercel.app

# APIs externes
GOOGLE_AI_API_KEY=your_gemini_key
SENDGRID_API_KEY=your_sendgrid_key
STRIPE_SECRET_KEY=your_stripe_key

# Base de données
SUPABASE_URL=https://project.supabase.co
SUPABASE_ANON_KEY=your_supabase_key

# Sécurité SSO
PHOENIX_SECRET_KEY=your_jwt_secret
PHOENIX_ENCRYPTION_KEY=your_encryption_key
```

### **Credentials n8n**
Créez ces credentials dans n8n :

1. **phoenix-config** (Generic Credential)
   - `website_url`: URL du site Phoenix
   - `n8n_webhook`: URL de base de vos webhooks
   - `premium_monthly`: Price ID Stripe mensuel
   - `premium_yearly`: Price ID Stripe annuel
   - `enterprise`: Price ID Stripe entreprise

2. **sendgrid-api** (HTTP Header Auth)
   - Authorization: `Bearer YOUR_SENDGRID_API_KEY`

3. **stripe-api** (HTTP Header Auth)
   - Authorization: `Bearer YOUR_STRIPE_SECRET_KEY`

## 🌐 **Architecture des workflows**

### **🎛️ Master Controller**
`phoenix-ecosystem-master-final.json` - Point d'entrée unique qui route vers :
- Génération de lettres
- Génération de CV  
- Gestion des paiements
- Inscription utilisateurs

### **💳 Ecosystem Stripe**
- `phoenix-stripe-checkout-creator.json` - Création sessions de paiement
- `phoenix-stripe-subscription-manager.json` - Gestion abonnements
- `phoenix-stripe-webhooks-complete.json` - Traitement événements Stripe

### **🔐 SSO System**
`phoenix-ecosystem-sso-integrated.json` - Authentication unifiée avec :
- JWT tokens chiffrés
- Navigation cross-apps sécurisée
- Synchronisation des profils

### **🤖 IA Generators**
- `phoenix-letters-generator.json` - Lettres de motivation IA
- `phoenix-cv-generator.json` - CV optimisés ATS

## 📊 **Monitoring**

### **Health Checks**
`phoenix-health-check-workflow.json` surveille :
- ✅ Disponibilité des microservices
- ✅ Santé des APIs externes
- ✅ Performance des workflows

### **Quotas**
`phoenix-quota-check-workflow.json` gère :
- 📈 Limites utilisateurs (free/premium)
- 📊 Métriques d'usage
- 🔄 Reset périodique

## 🚀 **Déploiement Cloud Run**

Les workflows sont **Cloud Run Ready** avec :
- URLs dynamiques via variables d'environnement
- Credentials sécurisés via système n8n
- Monitoring intégré
- Scalabilité automatique

## 📖 **Documentation complète**

- [📘 Guide d'installation n8n](PHOENIX_N8N_GUIDE.md)
- [🔐 Guide SSO complet](PHOENIX_SSO_GUIDE.md)
- [📋 Audit des workflows](PHOENIX_WORKFLOWS_AUDIT.md)

## 🤝 **Support**

- **Issues** : Utilisez les GitHub Issues pour signaler des problèmes
- **Documentation** : Consultez les guides dans `/docs/`
- **Architecture** : Voir `PHOENIX_WORKFLOWS_AUDIT.md`

## 📄 **Licence**

MIT License - voir [LICENSE](LICENSE) pour plus de détails.

---

**🔥 Phoenix Ecosystem - Révolutionnez vos reconversions professionnelles !**