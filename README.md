# Soluções digitais para mobilidade e agenda acadêmica — UNIFAL-MG

Código-fonte dos dois aplicativos do Trabalho de Conclusão de Curso
**"Transformando a experiência estudantil: soluções digitais para mobilidade e automação de agenda acadêmica"**
(Bacharelado Interdisciplinar em Ciência e Tecnologia — UNIFAL-MG, campus Poços de Caldas, 2026).

- **Autores:** Vitor Garcia Guerini e Pedro Affonso de Souza
- **Orientadora:** Profa. Marina Gomes Murta Moreno

| Pasta | Aplicativo | No ar |
|---|---|---|
| [`caronas-unifal/`](caronas-unifal/) | **Caronas UNIFAL** — oferta e reserva de caronas entre estudantes (PWA em Next.js + Supabase) | https://app-caronas-seven.vercel.app |
| [`semestre/`](semestre/) | **Semestre** — agenda acadêmica: lê a grade horária e os programas de ensino e envia os compromissos ao Google Agenda ou a um arquivo `.ics` | https://app-agendas.vercel.app |

## Onde está cada coisa

**Caronas UNIFAL** (`caronas-unifal/`)
- Banco, regras de reserva e segurança (RLS, funções transacionais): `supabase/migrations/`
- Telas e regras no servidor: `src/`
- Testes unitários: `tests/unit/` · integração com o banco: `scripts/concurrency-test.mjs` · carga: `scripts/load-test.mjs`
- Resultados dos testes: [`docs/TEST_REPORT.md`](caronas-unifal/docs/TEST_REPORT.md)
- Agentes de IA usados no desenvolvimento e na auditoria: `.claude/agents/` e `CLAUDE.md`

**Semestre** (`semestre/`)
- Leitura de planilhas e PDFs, geração de eventos e envio ao Google Agenda: `src/`
- Testes unitários (Vitest) e de navegador (Playwright): `tests/`
- Integração contínua (roda os testes a cada envio ao GitHub): `.github/workflows/ci.yml`
- Validação e registros para o TCC: [`docs/validacao.md`](semestre/docs/validacao.md), [`docs/tcc/`](semestre/docs/tcc/)

## Como rodar os testes

```bash
# Caronas UNIFAL
cd caronas-unifal && npm ci && npm run test      # unitários
# integração e carga usam um projeto Supabase próprio: copie .env.example para .env.local e preencha

# Semestre
cd semestre && npm ci && npm run test            # unitários
npx playwright install chromium && npm run build && npm run test:e2e   # navegador
```

## Sobre esta cópia

Cópia do código na versão usada no TCC (17/11/2026). Não contém senhas, chaves nem dados pessoais:
os valores de configuração ficam fora do repositório (`.env.local`), e os arquivos `.env.example`
mostram só os nomes. O identificador do cliente OAuth em `semestre/.env.production` é público por
natureza (aparece no site publicado). Os documentos de exemplo da agenda são sintéticos.
