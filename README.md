Explicação do código
1. Scanner
Scanner entrada = new Scanner(System.in);

O Scanner é usado para receber o que o usuário digitar no teclado.

No programa, ele é usado para receber a senha:

String senha = entrada.nextLine();

O nextLine() pega a linha inteira que foi digitada e guarda dentro da variável senha.

2. Repetição com do-while
do {
    System.out.print("Digite uma senha: ");
    String senha = entrada.nextLine();

    resultado = avaliarSenha(senha);
    System.out.println(resultado);

} while (!resultado.equals(SUCESSO));

O do-while faz o programa repetir a pergunta enquanto a senha não for aprovada.

O ! significa "não".

Então:

!resultado.equals(SUCESSO)

significa:

"Enquanto o resultado NÃO for igual a SUCESSO, continue pedindo outra senha."

Quando o resultado for SUCESSO, a condição fica falsa e o programa para.

3. Método avaliarSenha
public static String avaliarSenha(String senha)

Esse método é responsável por verificar a senha.

Ele recebe uma String chamada senha e retorna outra String com o resultado.

Por exemplo:

resultado = avaliarSenha(senha);

A senha é enviada para o método e ele verifica todas as regras.

4. Verificação dos 8 caracteres
if (senha.length() < 8) {
    return "DICA: A senha deve ter no mínimo 8 caracteres.";
}

Aqui é usado:

senha.length()

O length() conta quantos caracteres existem na senha.

O símbolo < significa "menor que".

Então:

senha.length() < 8

significa:

"A quantidade de caracteres da senha é menor que 8?"

Se for verdade, o programa retorna a mensagem e não continua para as próximas regras.

Exemplo:

Abcdef1

Tem 7 caracteres.

Então:

7 < 8

é verdadeiro, e a senha é rejeitada.

Já:

Abcdefg1

Tem 8 caracteres.

Então:

8 < 8

é falso, e o programa continua.

5. Verificação de número

Primeiro é criada uma variável:

boolean temNumero = false;

boolean só pode ter dois valores:

true = verdadeiro
false = falso

No começo, o programa considera que a senha ainda não possui número.

Depois, é usado um for:

for (int i = 0; i < senha.length(); i++) {
    if (Character.isDigit(senha.charAt(i))) {
        temNumero = true;
    }
}

O for passa por cada caractere da senha.

i = 0

Começa pelo primeiro caractere.

i < senha.length()

Enquanto o número da posição for menor que o tamanho da senha, o for continua.

i++

Depois de verificar um caractere, o i aumenta 1 e passa para o próximo.

senha.charAt(i)

O charAt() pega o caractere que está naquela posição.

Por exemplo, na senha:

Abcdefg1

o último caractere é o número 1.

Character.isDigit()

Essa função verifica se o caractere é um número.

Se encontrar um número:

temNumero = true;

A variável passa a indicar que a senha possui pelo menos um número.

Depois do for, temos:

if (!temNumero) {
    return "DICA: Adicione pelo menos um número à sua senha.";
}

O ! significa "não".

Então:

!temNumero

significa:

"Não tem número?"

Se não tiver, a senha é rejeitada.

6. Lista de senhas óbvias

O programa cria um vetor:

String[] senhasObvias = {"12345678", "senha123", "admin123"};

Esse vetor guarda as três senhas que não podem ser utilizadas.

Depois, outro for passa por cada uma delas:

for (int i = 0; i < senhasObvias.length; i++) {
    if (senha.equals(senhasObvias[i])) {
        return "ALERTA: Esta senha é muito comum ou óbvia.";
    }
}

O senhasObvias.length informa quantos itens existem no vetor.

O equals() é usado para comparar duas Strings.

Por exemplo:

senha.equals(senhasObvias[i])

significa:

"A senha digitada é igual a esta senha que está no vetor?"

Se for igual, o programa mostra o alerta.

7. Verificação de letra maiúscula

Primeiro:

boolean temMaiuscula = false;

Assim como no número, começa como false, porque ainda não encontramos uma letra maiúscula.

Depois:

for (int i = 0; i < senha.length(); i++) {
    if (Character.isUpperCase(senha.charAt(i))) {
        temMaiuscula = true;
    }
}

O for passa novamente por cada caractere da senha.

A função:

Character.isUpperCase()

verifica se o caractere é uma letra maiúscula.

Por exemplo:

A

é maiúscula.

Enquanto:

a

é minúscula.

Se encontrar uma letra maiúscula, a variável muda para:

temMaiuscula = true;

Depois:

if (!temMaiuscula) {
    return "DICA: Adicione pelo menos uma letra maiúscula à sua senha.";
}

Se não tiver nenhuma letra maiúscula, a senha é rejeitada.

8. Retorno de sucesso

Se a senha passar por todas as verificações anteriores, chega nesta parte:

return SUCESSO;

Isso significa que nenhuma regra foi quebrada.

A mensagem armazenada na variável SUCESSO é:

SUCESSO: Sua senha passou nos critérios básicos!
