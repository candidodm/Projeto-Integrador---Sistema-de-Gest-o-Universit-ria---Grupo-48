# Diagrama de Classes - Sistema Universitário

**Projeto Integrador - Fase 1**  
**Grupo 48**

---

## Diagrama de Classes

```
                         ┌─────────────────────────┐
                         │     <<abstract>>        │
                         │        Pessoa           │
                         ├─────────────────────────┤
                         │ # email: String         │
                         │ # telefone: String      │
                         │ # endereco: String      │
                         │ # cidade: String        │
                         │ # estado: String        │
                         │ # cep: String           │
                         │ # dataCadastro: DateTime│
                         │ # dataAtualizacao: DateTime│
                         │ # ativo: boolean        │
                         ├─────────────────────────┤
                         │ + validarDados(): boolean│
                         │ + getInformacoes(): String│
                         └────────────┬────────────┘
                                      │
                        ┌─────────────┴─────────────┐
                        │                           │
                        │                           │
          ┌─────────────▼──────────┐    ┌──────────▼─────────────┐
          │    PessoaFisica        │    │   PessoaJuridica       │
          ├────────────────────────┤    ├────────────────────────┤
          │ - cpf: String          │    │ - cnpj: String         │
          │ - nome: String         │    │ - razaoSocial: String  │
          │ - dataNascimento: Date │    │ - nomeFantasia: String │
          │ - nomePai: String      │    │ - dataAbertura: Date   │
          │ - nomeMae: String      │    │ - inscricaoEstadual: String│
          │ - rg: String           │    │ - ramoAtividade: String│
          │ - observacoes: String  │    │ - observacoes: String  │
          ├────────────────────────┤    ├────────────────────────┤
          │ + calcularIdade(): int │    │ + calcularTempoAtividade(): int│
          │ + validarDados(): boolean│  │ + validarDados(): boolean│
          │ + getInformacoes(): String│ │ + getInformacoes(): String│
          └────────────┬───────────┘    └──────────┬─────────────┘
                       │                           │
         ┌─────────────┴──────────┐                │
         │                        │                │
         │                        │                │
┌────────▼──────────┐   ┌─────────▼────────┐   ┌─▼────────────────┐
│    Professor      │   │      Aluno       │   │   Fornecedor     │
├───────────────────┤   ├──────────────────┤   ├──────────────────┤
│ - matricula: String│  │ - matricula: String│ │ - setorAtuacao: String│
│ - departamento: String│ │ - curso: String │ │ - tipoProdutoServico: String│
│ - titulacao: String│  │ - turno: String  │   │ - produtosServicos: String│
│ - regimeTrabalho: String│ │ - periodo: int│  │ - condicoesPagamento: String│
│ - dataAdmissao: Date│ │ - status: StatusAluno│ │ - prazoEntrega: int│
│ - areaEspecializacao: String│ │ - dataMatricula: Date│ │ - nomeContato: String│
│ - curriculoLattes: String│ │ - formaIngresso: String│ │ - telefoneContato: String│
│ - salario: double │   │ - tipoBolsa: String│ │ - emailContato: String│
│ - ativo: boolean  │   │ - coeficienteRendimento: double│ │ - aprovado: boolean│
├───────────────────┤   ├──────────────────┤   │ - avaliacaoMedia: double│
│ + calcularTempoServico(): int│ │ + calcularTempoCurso(): int│ ├──────────────────┤
│ + aptoProgressao(): boolean│ │ + aptoMatricula(): boolean│ │ + aprovar(): void│
│ + validarDados(): boolean│ │ + matricularProximoPeriodo(): void│ │ + reprovar(): void│
│ + getInformacoes(): String│ │ + trancarMatricula(): void│ │ + adicionarAvaliacao(nota): void│
└───────────────────┘   │ + reativarMatricula(): void│ │ + isConfiavel(): boolean│
                        │ + validarDados(): boolean│ │ + validarDados(): boolean│
                        │ + getInformacoes(): String│ │ + getInformacoes(): String│
                        └──────────────────┘   └──────────────────┘
```

---

## Descrição das Classes

### 📌 Pessoa (Classe Abstrata Base)

**Responsabilidade:** Classe abstrata que define os atributos e comportamentos comuns a todas as pessoas no sistema.

**Atributos:**
- `email`: Endereço de e-mail
- `telefone`: Número de telefone
- `endereco`: Endereço completo
- `cidade`: Cidade de residência
- `estado`: Estado (UF)
- `cep`: Código postal
- `dataCadastro`: Data de criação do registro
- `dataAtualizacao`: Data da última atualização
- `ativo`: Status do cadastro (ativo/inativo)

**Métodos Abstratos:**
- `validarDados()`: Valida os dados da pessoa
- `getInformacoes()`: Retorna informações resumidas

**Tipo:** Abstrata (não pode ser instanciada)

---

### 👤 PessoaFisica

**Herda de:** Pessoa

**Responsabilidade:** Representa uma pessoa física no sistema.

**Atributos Específicos:**
- `cpf`: CPF (11 dígitos)
- `nome`: Nome completo
- `dataNascimento`: Data de nascimento
- `nomePai`: Nome do pai
- `nomeMae`: Nome da mãe
- `rg`: Número do RG
- `observacoes`: Observações gerais

**Métodos Específicos:**
- `calcularIdade()`: Calcula idade em anos
- `validarDados()`: Valida CPF e dados obrigatórios
- `getInformacoes()`: Retorna resumo com nome e CPF

---

### 🏢 PessoaJuridica

**Herda de:** Pessoa

**Responsabilidade:** Representa uma empresa ou organização.

**Atributos Específicos:**
- `cnpj`: CNPJ (14 dígitos)
- `razaoSocial`: Razão social da empresa
- `nomeFantasia`: Nome fantasia
- `dataAbertura`: Data de abertura da empresa
- `inscricaoEstadual`: Inscrição estadual
- `ramoAtividade`: Ramo de atividade
- `observacoes`: Observações gerais

**Métodos Específicos:**
- `calcularTempoAtividade()`: Calcula anos de atividade
- `validarDados()`: Valida CNPJ e dados obrigatórios
- `getInformacoes()`: Retorna resumo com nome e CNPJ

---

### 👨‍🏫 Professor

**Herda de:** PessoaFisica

**Responsabilidade:** Representa um professor da instituição.

**Atributos Específicos:**
- `matricula`: Número de matrícula funcional
- `departamento`: Departamento ao qual pertence
- `titulacao`: Nível de formação (graduação, mestrado, doutorado)
- `regimeTrabalho`: Tipo de regime (dedicação exclusiva, 40h, etc)
- `dataAdmissao`: Data de entrada na instituição
- `areaEspecializacao`: Área de especialização
- `curriculoLattes`: Link do Currículo Lattes
- `salario`: Salário base
- `ativo`: Se está ativo no quadro

**Métodos Específicos:**
- `calcularTempoServico()`: Calcula anos de serviço
- `aptoProgressao()`: Verifica se está apto para progressão
- `validarDados()`: Valida matrícula e dados profissionais
- `getInformacoes()`: Retorna resumo profissional

**Enumerações:**
- `Titulacao`: GRADUACAO, ESPECIALIZACAO, MESTRADO, DOUTORADO, POS_DOUTORADO
- `RegimeTrabalho`: DEDICACAO_EXCLUSIVA, TEMPO_INTEGRAL, TEMPO_PARCIAL, HORISTA

---

### 🎓 Aluno

**Herda de:** PessoaFisica

**Responsabilidade:** Representa um estudante matriculado.

**Atributos Específicos:**
- `matricula`: Número de matrícula acadêmica
- `curso`: Curso matriculado
- `turno`: Turno das aulas (matutino, vespertino, noturno)
- `periodo`: Período/semestre atual
- `status`: Situação da matrícula (ativo, trancado, formado)
- `dataMatricula`: Data de matrícula inicial
- `formaIngresso`: Como ingressou (vestibular, ENEM, etc)
- `tipoBolsa`: Tipo de bolsa (integral, parcial, nenhuma)
- `coeficienteRendimento`: CR (0 a 10)

**Métodos Específicos:**
- `calcularTempoCurso()`: Calcula tempo no curso
- `aptoMatricula()`: Verifica se pode se matricular
- `matricularProximoPeriodo()`: Avança período
- `trancarMatricula()`: Tranca a matrícula
- `reativarMatricula()`: Reativa matrícula trancada
- `validarDados()`: Valida dados acadêmicos
- `getInformacoes()`: Retorna resumo acadêmico

**Enumerações:**
- `StatusAluno`: ATIVO, TRANCADO, FORMADO, DESISTENTE, TRANSFERIDO
- `Turno`: MATUTINO, VESPERTINO, NOTURNO, INTEGRAL

---

### 📦 Fornecedor

**Herda de:** PessoaJuridica

**Responsabilidade:** Representa um fornecedor de produtos/serviços.

**Atributos Específicos:**
- `setorAtuacao`: Setor de atuação
- `tipoProdutoServico`: Se fornece produtos, serviços ou ambos
- `produtosServicos`: Descrição do que fornece
- `condicoesPagamento`: Condições de pagamento
- `prazoEntrega`: Prazo médio de entrega (dias)
- `nomeContato`: Nome do representante
- `telefoneContato`: Telefone do contato
- `emailContato`: E-mail do contato
- `aprovado`: Se está aprovado para fornecer
- `avaliacaoMedia`: Média de avaliações (0 a 10)

**Métodos Específicos:**
- `aprovar()`: Aprova o fornecedor
- `reprovar()`: Reprova o fornecedor
- `adicionarAvaliacao()`: Adiciona uma avaliação
- `isConfiavel()`: Verifica se é confiável (nota >= 7)
- `validarDados()`: Valida dados de fornecimento
- `getInformacoes()`: Retorna resumo comercial

**Enumerações:**
- `SetorAtuacao`: TECNOLOGIA, MOBILIARIO, LIMPEZA, ALIMENTACAO, etc
- `TipoProdutoServico`: PRODUTOS, SERVICOS, AMBOS

---

## Relacionamentos

### Herança (Generalização/Especialização)

```
Pessoa (abstrata)
    ├── PessoaFisica
    │   ├── Professor
    │   └── Aluno
    └── PessoaJuridica
        └── Fornecedor
```

**Explicação:**
- `PessoaFisica` e `PessoaJuridica` **herdam** de `Pessoa`
- `Professor` e `Aluno` **herdam** de `PessoaFisica`
- `Fornecedor` **herda** de `PessoaJuridica`

### Características da Herança

- **Reutilização de código**: Classes filhas herdam atributos e métodos da classe pai
- **Polimorfismo**: Cada classe implementa `validarDados()` e `getInformacoes()` de forma específica
- **Abstração**: A classe `Pessoa` não pode ser instanciada diretamente

---

## Classes Utilitárias (Suporte)

### 🔧 ValidadorCPF

**Responsabilidade:** Validar números de CPF.

**Métodos:**
- `validar(cpf: String): boolean` - Valida CPF
- `formatar(cpf: String): String` - Formata CPF (000.000.000-00)

### 🔧 ValidadorCNPJ

**Responsabilidade:** Validar números de CNPJ.

**Métodos:**
- `validar(cnpj: String): boolean` - Valida CNPJ
- `formatar(cnpj: String): String` - Formata CNPJ (00.000.000/0000-00)

---

**Documento criado em:** Outubro 2025  
**Versão:** 1.0  
**Status:** Aprovado
