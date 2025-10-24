# 🌾 Grain6pbc Grainbranch Structure Guide

**Standardized grainbranch structure for all grain6pbc repositories**

## 🎯 **Grainbranch Structure**

All grain6pbc repositories follow this structure:

```
grain6pbc/
├── grain6/                    # Main template repository
│   ├── grain6-get-started/     # Getting started guide
│   ├── grain6-humble-stack/    # Humble Stack documentation
│   ├── grain6-sixos/           # SixOS integration guide
│   └── grain6-production/      # Production deployment guide
├── grainkae3g/                # Personal instance
│   ├── grain6-get-started-12025-10-24--1033--PDT--moon-vishakha------asc-gem000--sun-11th--kae3g/
│   └── [future grainbranches]
├── graincontacts/              # Global identity system
│   ├── graincontacts-v1/       # Version 1 implementation
│   └── graincontacts-v2/       # Version 2 with enhanced features
├── humble-stack/               # Humble UI applications
│   ├── humble-stack-desktop/   # Desktop applications
│   ├── humble-stack-mobile/    # Mobile applications (future)
│   └── humble-stack-web/       # Web applications (future)
└── graindaemon/                # Automation system
    ├── graindaemon-v1/         # Current automation system
    └── graindaemon-v2/         # Enhanced automation (future)
```

## 🌐 **Grainsite URL Structure**

Each grainbranch gets its own subdirectory URL:

```
https://grain6pbc.github.io/{repo-name}/{grainbranch-name}/
```

### **Examples:**
- **grain6**: `https://grain6pbc.github.io/grain6/grain6-get-started/`
- **grainkae3g**: `https://grain6pbc.github.io/grainkae3g/grain6-get-started-12025-10-24--1033--PDT--moon-vishakha------asc-gem000--sun-11th--kae3g/`
- **graincontacts**: `https://grain6pbc.github.io/graincontacts/graincontacts-v1/`
- **humble-stack**: `https://grain6pbc.github.io/humble-stack/humble-stack-desktop/`

## 🔄 **GitHub Actions Workflow**

All repositories use the same GitHub Actions workflows:

### **1. grainpath-sync.yml**
- Syncs grainbranch to main
- Updates GitHub repository description
- Triggers deployment

### **2. deploy.yml**
- Builds and deploys to GitHub Pages
- Updates repository description with grainsite URL
- Handles SvelteKit build process

## 📋 **Grainbranch Naming Convention**

### **Format:**
```
{project-name}-{version}-{graintime}-{author}
```

### **Examples:**
- `grain6-get-started-12025-10-24--1033--PDT--moon-vishakha------asc-gem000--sun-11th--kae3g`
- `graincontacts-v1-12025-10-25--0900--PDT--moon-anuradha------asc-gem015--sun-09th--kae3g`
- `humble-stack-desktop-12025-10-26--1400--PDT--moon-pushya------asc-gem030--sun-12th--kae3g`

### **Components:**
- **Project Name**: `grain6-get-started`, `graincontacts-v1`, etc.
- **Graintime**: `12025-10-24--1033--PDT--moon-vishakha------asc-gem000--sun-11th`
- **Author**: `kae3g` (or other grain sheaf)

## 🎨 **Repository Description Format**

All repositories use this description format:

```
🌾 Grain6pbc {Project}: {Grainbranch} | Live Site: {Grainsite URL} | Session {Number} Complete
```

### **Examples:**
- `🌾 Grain6pbc Template: grain6-get-started | Live Site: https://grain6pbc.github.io/grain6/grain6-get-started/ | Session 780 Complete`
- `🌾 Grain6pbc Personal: grain6-get-started-12025-10-24--1033--PDT--moon-vishakha------asc-gem000--sun-11th--kae3g | Live Site: https://grain6pbc.github.io/grainkae3g/grain6-get-started-12025-10-24--1033--PDT--moon-vishakha------asc-gem000--sun-11th--kae3g/ | Session 780 Complete`

## 🔧 **Implementation Steps**

### **1. Create Repository Structure**
```bash
# Create main template repository
gh repo create grain6pbc/grain6 --public --template

# Create personal instance
gh repo create grain6pbc/grainkae3g --public

# Create other repositories
gh repo create grain6pbc/graincontacts --public
gh repo create grain6pbc/humble-stack --public
gh repo create grain6pbc/graindaemon --public
```

### **2. Set Up GitHub Actions**
Each repository needs:
- `.github/workflows/grainpath-sync.yml`
- `.github/workflows/deploy.yml`
- `.github/workflows/mirror-sync.yml` (for mirror repositories)

### **3. Configure Graindaemon**
Each repository needs:
- `grainstore/graindaemon/src/graindaemon/github-description-sync.bb`
- `grainstore/graindaemon/src/graindaemon/humble-sync.bb`
- `grainstore/grainbarrel/bb.edn` with graindaemon tasks

### **4. Set Up Mirror Synchronization**
- `grain6pbc/*` → `grain6/*` (main mirror)
- `grain6pbc/*` → `grainkae3g/*` (personal mirror)
- `grain6pbc/*` → `grainkae3g/*` (community mirror)

## 🌐 **Domain Strategy**

### **Primary Domains:**
- `grain6.network` → Main Grain Network site
- `grain6pbc.org` → Organization site
- `kae3g.grain6.network` → Personal subdomain

### **GitHub Pages Domains:**
- `grain6pbc.github.io` → Main organization
- `grain6.github.io` → Mirror organization
- `kae3g.github.io` → Personal organization

## 📚 **Documentation Structure**

Each repository follows this documentation structure:

```
docs/
├── core/philosophy/
│   ├── PSEUDO.md              # Core philosophical foundations
│   └── TODO-ASPIRATIONAL.md   # Future goals and vision
├── architecture/
│   ├── HUMBLE-STACK.md        # Humble Stack architecture
│   ├── SIXOS-INTEGRATION.md   # SixOS integration
│   └── GRAINDAEMON-SYSTEM.md  # Graindaemon automation
├── guides/
│   ├── GETTING-STARTED.md     # Beginner's guide
│   ├── DEVELOPMENT-WORKFLOW.md # Best practices
│   └── DEPLOYMENT.md          # Production deployment
└── reference/
    ├── API.md                 # API documentation
    ├── CONFIGURATION.md       # Configuration options
    └── TROUBLESHOOTING.md     # Common issues and solutions
```

## 🔄 **Synchronization Strategy**

### **1. Template → Instance**
- `grain6pbc/grain6` → `grain6pbc/grainkae3g`
- Automated via GitHub Actions
- Personal content preserved

### **2. Organization → Mirror**
- `grain6pbc/*` → `grain6/*`
- Automated via GitHub Actions
- Community content preserved

### **3. Cross-Organization Sync**
- `grain6pbc/*` → `kae3g/*`
- Automated via GitHub Actions
- Personal content preserved

## 🎯 **Benefits**

1. **Consistency**: All repositories follow the same structure
2. **Automation**: GitHub Actions handle synchronization
3. **Scalability**: Easy to add new repositories
4. **Maintainability**: Centralized configuration
5. **Community**: Shared templates and best practices

## 🚀 **Next Steps**

1. **Create grain6pbc/grain6 template repository**
2. **Set up GitHub Actions workflows**
3. **Configure graindaemon system**
4. **Create mirror repositories**
5. **Set up synchronization**
6. **Deploy and test**

This structure ensures all grain6pbc repositories follow the same grainbranch pattern, making them easy to manage and scale.
