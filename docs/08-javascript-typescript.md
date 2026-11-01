# 08 — JavaScript Avançado e TypeScript

**Exigência documental:** enunciado pp. 9–10. Exemplos **conceituais**, não aplicação implementada.

## Decisões técnicas
- **Tipagem forte:** TypeScript com strict mode; DTOs de entrada e saída explícitos.
- **Interfaces:** ports abstraem persistência, clock e integrações futuras.
- **Classes:** entidades/agregados com invariantes; objetos de valor imutáveis.
- **Enums ou literal unions:** status e classificações acordados pelo time; não atribuir categorias regulamentares sem fonte.
- **Funções puras:** validações determinísticas de quantidade e status.
- **Módulos ES6+:** isolamento de dependências.
- **Async/await:** chamadas futuras a repositórios/APIs, com captura de erros.
- **Generics:** abstrações como Repository<T, ID>, apenas quando úteis.
- **Erros:** erros de domínio explícitos, traduzidos na camada externa.
- **Contratos compartilhados:** interfaces e tipos em camada pública bem definida.

## Exemplo de tipos, interface, classe e função
~~~typescript
export type StatusCarga =
  | "REGISTRADA" | "AGUARDANDO_DOCUMENTACAO"
  | "EM_ANALISE" | "EM_INSPECAO" | "LIBERADA"
  | "BLOQUEADA" | "EM_MOVIMENTACAO"
  | "FINALIZADA" | "CANCELADA";

export interface RegistrarCargaInput {
  produtoQuimicoId: string;
  classificacaoRisco: string;
  quantidade: number;
  unidade: string;
  responsavelTecnicoId: string;
}

export function quantidadeValida(quantidade: number): boolean {
  return Number.isFinite(quantidade) && quantidade > 0;
}

export interface Repository<T, ID = string> {
  findById(id: ID): Promise<T | null>;
  save(entity: T): Promise<void>;
}

export class RegraNegocioError extends Error {
  constructor(
    public readonly code: string,
    message: string,
  ) {
    super(message);
    this.name = "RegraNegocioError";
  }
}
~~~

A união de status acima é **proposta** (não um enum imposto pela FIAP). O exemplo não substitui validação de unidade/legislação aplicável e não está conectado a dados reais.
