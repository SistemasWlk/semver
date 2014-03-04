Semantic Versioning 2.0.0
=========================

Semântico
---------

"Palavra que indica a origem hipotética de formação da mesma, verdadeiro significado criado pelo homem para indicar procedencia. Semân = Semêm, fonte geradora.
antica = antigo, anterior, antes, procedencia original.

Seman = Sêmen
Antica = Antiga, anterior, antecedente, procedencia original."

Versionamento
-------------

"Um sistema de controle de versão (ou versionamento), VCS (do inglês version control system) ou ainda SCM (do inglês source code management) na função prática da Ciência da Computação e da Engenharia de Software, é um software com a finalidade de gerenciar diferentes versões no desenvolvimento de um documento qualquer. Esses sistemas são comumente utilizados no desenvolvimento de software para controlar as diferentes versões — histórico e desenvolvimento — dos códigos-fontes e também da documentação."
Fontes: http://pt.wikipedia.org

Introdução
----------
No mundo do gerenciamento de software, existe um lugar terrível chamado “dependency hell“. Quanto mais o seu sistema cresce e mais pacotes você integrar no seu software, maior a probabilidade de você se encontrar, um dia, neste poço do desespero.

Em sistemas com muitas dependências, liberar novos pacotes de versões pode rapidamente se tornar um pesadelo. Se as especificações de dependência são muito apertadas, você corre perigo de “version lock” (a incapacidade para atualizar um pacote sem ter que lançar novas versões de cada pacote dependente). Se as dependências são especificadas muito vagamente, você inevitavelmente será mordido por “version promiscuity” (assumindo compatibilidade com versões futuras sem ter certeza). O dependency hell é onde você está quando o version lock e/ou version promiscuity impe-ode mover o projeto adiante de forma fácil e segura.

Como uma solução para este problema, proponho um simples conjunto de regras e requisitos que ditam como números de versão são atribuídos e incrementados. Para que este sistema funcione, você primeiro precisa declarar uma API pública. Esta pode consistir de documentação ou ser executada pelo próprio código. Independentemente disso, é importante que essa API seja clara e precisa. Depois de identificar a sua API pública, você comunica alterações nela com incrementos específicos para o seu número de versão. Considere uma versão no formato XYZ (Major.Minor.Patch). Correções de bugs que não afetam o aumento da API incrementar patch versão, adições/mudanças da API compatível  com versões anteriores incrementar minor versão, e as mudanças API  incompatíveis com versões anteriores incrementar a major versão.

Eu chamo este sistema “Semantic Versioning”. No âmbito deste regime, números de versão e a forma como muda transmite um significado sobre o código subjacente e que tem sido modificado de uma versão para a próxima.

Especificações Versão Semântica
(Semantic Versioning Specification - SemVer)
Software que usa Semantic Versioning DEVE declarar a public API. Essa API pode ser declarada no código ou existir em documentação. Quando for feita, ela deverá ser precisa e compreensiva.
Um número de versão normal DEVE ter a forma de X.Y.Z, onde X,Y e Z são inteiros. X é o major version, y é o minor version e Z é o patch version. Cada elemento DEVE aumentar numericamente. Por exemplo: 1.9.0 < 1.10.0 < 1.11.0.
Um número de versão especial PODE ser denominado ao adicionar uma string abritrária logo após o patch version. Essa string DEVE conter somente alfanuméricos mais o símbolo menos [0-9A-Za-z-] e DEVE começar com um caracter alpha [A-Za-z]. Versões especiais devem satisfazer e ter menor precedência que a versão normal associada. Precedência DEVE ser determinada pela ordenação lexicográfica ASCII. Exemplo: 1.0.0beta1 < 1.0.0beta2 < 1.0.0
Uma vez que foi lançada uma versão, o conteúdo daquela versão NÃO DEVE ser modificada. Qualquer modificação deve ser lançada como uma nova versão.
Major version que começe com 0 (0.y.z) é para desenvolvimento inicial. Qualquer coisa pode mudar a qualquer momento. A public API não pode ser considerada estável.
A Versão 1.0.0 define a public API. A maneira com que o número de versão aumenta é agora dependente dessa API e em como ela muda.
Patch version Z (x.y.Z | x > 0) DEVE ser incrementada se somente bug fixes que são compatíveis com versões anteriores são introduzidos. Um bug fix é definido como uma mudança interna que corrige um comportamento incorreto.
Minor Version Y (x.Y.z | x > 0) DEVE ser incrementada se novas funcionalidades que são compatíveis com versões anteriores são introduzidas à public API. Ela PODE ser incrementada se muitas novas funcionalidades ou melhorias forem introduzidas no código privado. Ela PODE incluir patches.
Major version X (X.y.z | X > 0) DEVE ser incrementada se qualquer mudança que quebre a compatibilidade com versões anteriores são introduzidas na public API. Ela PODE incluir mudanças minor e de patch.
