#include <stdio.h>
#include <string.h>
#include <conio.h>

// Função para esconder a senha durante a digitação
void get_password(char *password) {
    char ch;
    int i = 0;

    while (1) {
        ch = _getch();
        if (ch == 13) { // Enter key
            password[i] = '\0';
            break;
        } else if (ch == 8) { // Backspace key
            if (i > 0) {
                i--;
                printf("\b \b");
            }
        } else {
            password[i++] = ch;
            printf("*");
        }
    }
}

// Função para verificar as credenciais
int verificar_credenciais(const char *usuario, const char *senha) {
    // Para simplificação, utilizamos credenciais fixas
    const char usuario_correto[] = "admin";
    const char senha_correta[] = "1234";

    if (strcmp(usuario, usuario_correto) == 0 && strcmp(senha, senha_correta) == 0) {
        return 1; // Credenciais corretas
    } else {
        return 0; // Credenciais incorretas
    }
}

int main() {
    char usuario[50];
    char senha[50];
    int tentativas = 3;

    while (tentativas > 0) {
        printf("Usuario: ");
        scanf("%s", usuario);

        printf("Senha: ");
        get_password(senha);
        printf("\n");

        if (verificar_credenciais(usuario, senha)) {
            printf("Login bem-sucedido!\n");
            // Continue com a lógica do p  rograma aqui
            break;
        } else {
            printf("Usuario ou senha incorretos. Tente novamente.\n");
            tentativas--;
        }

        if (tentativas == 0) {
            printf("Numero de tentativas excedido. Programa encerrado.\n");
        }
    }

    return 0;
}

<!---
JoTinha0021/JoTinha0021 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
