# Diagrama de Caso de Uso - Sistema Universitário

**Projeto Integrador - Fase 1**  
**Grupo 48**

---

## Diagrama

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│                    SISTEMA UNIVERSITÁRIO                        │
│                                                                 │
│                                                                 │
│                                                                 │
│      ┌──────────────────┐                                      │
│      │                  │                                      │
│      │                  │                                      │
│      │  Administrador   │────────────▶ (Cadastrar Pessoa Física)│
│      │                  │                                      │
│      │                  │────────────▶ (Cadastrar Pessoa Jurídica)│
│      │                  │                                      │
│      │                  │────────────▶ (Cadastrar Professor)   │
│      │                  │                                      │
│      │                  │────────────▶ (Cadastrar Aluno)       │
│      │                  │                                      │
│      │                  │────────────▶ (Cadastrar Fornecedor)  │
│      │                  │                                      │
│      └──────────────────┘                                      │
│                                                                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Atores

### 👤 Administrador
**Descrição:** Usuário responsável por gerenciar todos os cadastros do sistema universitário.

**Responsabilidades:**
- Cadastrar pessoas físicas no sistema
- Cadastrar pessoas jurídicas (empresas)
- Cadastrar professores da instituição
- Cadastrar alunos matriculados
- Cadastrar fornecedores de produtos e serviços

---

## Casos de Uso

### 1. 👤 Cadastrar Pessoa Física

**Descrição:** Permite o cadastro de dados básicos de pessoas físicas no sistema.

**Ator Principal:** Administrador

**Dados Cadastrados:**
- CPF (obrigatório)
- Nome completo (obrigatório)
- Data de nascimento (obrigatório)
- E-mail (obrigatório)
- Telefone (obrigatório)
- Endereço completo
- Observações

---

### 2. 🏢 Cadastrar Pessoa Jurídica

**Descrição:** Permite o cadastro de empresas e organizações no sistema.

**Ator Principal:** Administrador

**Dados Cadastrados:**
- CNPJ (obrigatório)
- Razão Social (obrigatório)
- Nome Fantasia (obrigatório)
- E-mail (obrigatório)
- Telefone (obrigatório)
- Inscrição Estadual
- Endereço completo
- Ramo de atividade
- Observações

---

### 3. 👨‍🏫 Cadastrar Professor

**Descrição:** Permite o cadastro de professores com informações pessoais e profissionais.

**Ator Principal:** Administrador

**Dados Cadastrados:**
- **Dados Pessoais:** (herda de Pessoa Física)
  - CPF, nome, data de nascimento, e-mail, telefone
- **Dados Profissionais:**
  - Matrícula (obrigatório)
  - Departamento (obrigatório)
  - Titulação (obrigatório)
  - Regime de trabalho (obrigatório)
  - Data de admissão (obrigatório)
  - Área de especialização
  - Currículo Lattes

---

### 4. 🎓 Cadastrar Aluno

**Descrição:** Permite o cadastro de alunos com informações acadêmicas.

**Ator Principal:** Administrador

**Dados Cadastrados:**
- **Dados Pessoais:** (herda de Pessoa Física)
  - CPF, nome, data de nascimento, e-mail, telefone
- **Dados Acadêmicos:**
  - Matrícula (obrigatório)
  - Curso (obrigatório)
  - Turno (obrigatório)
  - Período/Semestre (obrigatório)
  - Status (obrigatório)
  - Data de matrícula (obrigatório)
  - Forma de ingresso
  - Tipo de bolsa
  - Nome dos pais

---

### 5. 📦 Cadastrar Fornecedor

**Descrição:** Permite o cadastro de fornecedores de produtos e serviços.

**Ator Principal:** Administrador

**Dados Cadastrados:**
- **Dados da Empresa:** (herda de Pessoa Jurídica)
  - CNPJ, razão social, nome fantasia, e-mail, telefone
- **Dados de Fornecimento:**
  - Setor de atuação (obrigatório)
  - Tipo: Produtos/Serviços (obrigatório)
  - Descrição de produtos/serviços (obrigatório)
  - Condições de pagamento (obrigatório)
  - Prazo de entrega
  - Dados do contato (nome, telefone, e-mail)

---

## Relacionamentos

Todos os 5 casos de uso são executados pelo **Administrador**.

Não há relacionamentos de inclusão (<<include>>) ou extensão (<<extend>>) entre os casos de uso, pois cada um representa uma funcionalidade independente.

---

## Observações

- O sistema requer autenticação do administrador antes de acessar qualquer funcionalidade
- Todos os cadastros incluem validação de dados (CPF, CNPJ, e-mail)
- Os casos de uso de Professor, Aluno e Fornecedor estendem os conceitos de Pessoa Física e Pessoa Jurídica

---

**Documento criado em:** Novembro 2025  
**Versão:** 1.0  
**Status:** Aprovado
