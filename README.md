# 📱 Lista de Exercícios — Android Studio Java

Projeto desenvolvido em **Android Studio utilizando Java**, contendo 7 exercícios de formulários, eventos de clique, entrada de dados, validações e exibição de resultados.

---

## 📋 Exercício 1 — Pedido de Lanche

### Objetivo

A cantina recebe um pedido contendo:

* Lanche
* Bebida
* Observação

### IDs utilizados

* `etxtLanche`
* `etxtBebida`
* `etxtObservacao`
* `btn_Pedir`

### `activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp">

    <EditText
        android:id="@+id/etxtLanche"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Digite o lanche" />

    <EditText
        android:id="@+id/etxtBebida"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Digite a bebida" />

    <EditText
        android:id="@+id/etxtObservacao"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Digite uma observação" />

    <Button
        android:id="@+id/btn_Pedir"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Fazer pedido" />

    <TextView
        android:id="@+id/txtResultado"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:textSize="18sp" />

</LinearLayout>
```

### `MainActivity.java`

```java
package com.example.exerciciosandroid;

import android.os.Bundle;
import android.util.Log;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etxtLanche, etxtBebida, etxtObservacao;
    Button btn_Pedir;
    TextView txtResultado;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etxtLanche = findViewById(R.id.etxtLanche);
        etxtBebida = findViewById(R.id.etxtBebida);
        etxtObservacao = findViewById(R.id.etxtObservacao);
        btn_Pedir = findViewById(R.id.btn_Pedir);
        txtResultado = findViewById(R.id.txtResultado);

        btn_Pedir.setOnClickListener(v -> {

            String lanche = etxtLanche.getText().toString();
            String bebida = etxtBebida.getText().toString();
            String observacao = etxtObservacao.getText().toString();

            Log.d("PEDIDO", "Lanche: " + lanche);
            Log.d("PEDIDO", "Bebida: " + bebida);
            Log.d("PEDIDO", "Observação: " + observacao);

            String resultado = "Pedido: " + lanche + " + " + bebida +
                    " (" + observacao + ")";

            txtResultado.setText(resultado);
        });
    }
}
```

### Resultado esperado

```text
Pedido: X-Salada + Suco de laranja (sem tomate)
```

---

# 🐶 Exercício 2 — Cadastro de Pet

### Objetivo

Cadastrar um animal informando nome, espécie e idade.

### IDs

* `etxtNomePet`
* `etxtEspecie`
* `etxtIdadePet`
* `btn_CadastrarPet`

### `activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp">

    <EditText
        android:id="@+id/etxtNomePet"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Nome do pet" />

    <EditText
        android:id="@+id/etxtEspecie"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Espécie" />

    <EditText
        android:id="@+id/etxtIdadePet"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Idade"
        android:inputType="number" />

    <Button
        android:id="@+id/btn_CadastrarPet"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Cadastrar Pet" />

    <TextView
        android:id="@+id/txtResultado"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:textSize="18sp" />

</LinearLayout>
```

### `MainActivity.java`

```java
package com.example.exerciciosandroid;

import android.os.Bundle;
import android.util.Log;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etxtNomePet, etxtEspecie, etxtIdadePet;
    Button btn_CadastrarPet;
    TextView txtResultado;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etxtNomePet = findViewById(R.id.etxtNomePet);
        etxtEspecie = findViewById(R.id.etxtEspecie);
        etxtIdadePet = findViewById(R.id.etxtIdadePet);
        btn_CadastrarPet = findViewById(R.id.btn_CadastrarPet);
        txtResultado = findViewById(R.id.txtResultado);

        btn_CadastrarPet.setOnClickListener(v -> {

            String nome = etxtNomePet.getText().toString();
            String especie = etxtEspecie.getText().toString();
            String idade = etxtIdadePet.getText().toString();

            Log.d("PET", "Nome: " + nome);
            Log.d("PET", "Espécie: " + especie);
            Log.d("PET", "Idade: " + idade + " anos");

            txtResultado.setText(
                    nome + " (" + especie + "), " +
                    idade + " anos, cadastrado com sucesso!"
            );
        });
    }
}
```

### Resultado

```text
Thor (Cão), 4 anos, cadastrado com sucesso!
```

---

# 🏫 Exercício 3 — Reserva de Sala

### Objetivo

Registrar uma reserva de laboratório informando responsável, sala e horário.

### IDs

* `etxtNome`
* `etxtSala`
* `etxtHorario`
* `btn_Reservar`

### `activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp">

    <EditText
        android:id="@+id/etxtNome"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Nome do responsável" />

    <EditText
        android:id="@+id/etxtSala"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Sala" />

    <EditText
        android:id="@+id/etxtHorario"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Horário"
        android:inputType="time" />

    <Button
        android:id="@+id/btn_Reservar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Reservar" />

    <TextView
        android:id="@+id/txtResultado"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:textSize="18sp" />

</LinearLayout>
```

### `MainActivity.java`

```java
package com.example.exerciciosandroid;

import android.os.Bundle;
import android.util.Log;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etxtNome, etxtSala, etxtHorario;
    Button btn_Reservar;
    TextView txtResultado;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etxtNome = findViewById(R.id.etxtNome);
        etxtSala = findViewById(R.id.etxtSala);
        etxtHorario = findViewById(R.id.etxtHorario);
        btn_Reservar = findViewById(R.id.btn_Reservar);
        txtResultado = findViewById(R.id.txtResultado);

        btn_Reservar.setOnClickListener(v -> {

            String nome = etxtNome.getText().toString();
            String sala = etxtSala.getText().toString();
            String horario = etxtHorario.getText().toString();

            Log.d("RESERVA", "Responsável: " + nome);
            Log.d("RESERVA", "Sala: " + sala);
            Log.d("RESERVA", "Horário: " + horario);

            txtResultado.setText(
                    sala + " reservado para " + nome +
                    " às " + horario
            );
        });
    }
}
```

### Resultado

```text
Lab 3 reservado para Prof. Marcos às 19:00
```

---

# 🔐 Exercício 4 — Tela de Login

### Regra

A senha precisa possuir **no mínimo 6 caracteres**.

Se possuir menos:

```text
Senha muito curta! Mínimo 6 caracteres.
```

Se estiver correta:

```text
Login realizado: ana@email.com
```

### IDs

* `etxtEmail`
* `etxtSenha`
* `btn_Entrar`

### `activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp">

    <EditText
        android:id="@+id/etxtEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="E-mail"
        android:inputType="textEmailAddress" />

    <com.google.android.material.textfield.TextInputLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:endIconMode="password_toggle">

        <com.google.android.material.textfield.TextInputEditText
            android:id="@+id/etxtSenha"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Senha"
            android:inputType="textPassword" />

    </com.google.android.material.textfield.TextInputLayout>

    <Button
        android:id="@+id/btn_Entrar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Entrar" />

    <TextView
        android:id="@+id/txtResultado"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:textSize="18sp" />

</LinearLayout>
```

### `MainActivity.java`

```java
package com.example.exerciciosandroid;

import android.os.Bundle;
import android.util.Log;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etxtEmail, etxtSenha;
    Button btn_Entrar;
    TextView txtResultado;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etxtEmail = findViewById(R.id.etxtEmail);
        etxtSenha = findViewById(R.id.etxtSenha);
        btn_Entrar = findViewById(R.id.btn_Entrar);
        txtResultado = findViewById(R.id.txtResultado);

        btn_Entrar.setOnClickListener(v -> {

            String email = etxtEmail.getText().toString();
            String senha = etxtSenha.getText().toString();

            Log.d("LOGIN", "E-mail digitado: " + email);
            Log.d("LOGIN", "Senha com " + senha.length() + " caracteres");

            if (senha.length() < 6) {

                String mensagem =
                        "Senha muito curta! Mínimo 6 caracteres.";

                Log.d("LOGIN", mensagem);
                txtResultado.setText(mensagem);

            } else {

                Log.d("LOGIN", "Login realizado: " + email);

                txtResultado.setText(
                        "Bem-vindo(a), " + email + "!"
                );
            }
        });
    }
}
```

### Resultado válido

```text
Bem-vindo(a), ana@email.com!
```

### Resultado inválido

```text
Senha muito curta! Mínimo 6 caracteres.
```

---

# 🎫 Exercício 5 — Inscrição em Evento

### Regra

A idade deve estar entre **14 e 99 anos**.

### IDs

* `etxtNome`
* `etxtEmail`
* `etxtIdade`
* `btn_Inscrever`

### `activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp">

    <EditText
        android:id="@+id/etxtNome"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Nome" />

    <EditText
        android:id="@+id/etxtEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="E-mail"
        android:inputType="textEmailAddress" />

    <EditText
        android:id="@+id/etxtIdade"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Idade"
        android:inputType="number" />

    <Button
        android:id="@+id/btn_Inscrever"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Inscrever" />

    <TextView
        android:id="@+id/txtResultado"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:textSize="18sp" />

</LinearLayout>
```

### `MainActivity.java`

```java
package com.example.exerciciosandroid;

import android.os.Bundle;
import android.util.Log;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etxtNome, etxtEmail, etxtIdade;
    Button btn_Inscrever;
    TextView txtResultado;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etxtNome = findViewById(R.id.etxtNome);
        etxtEmail = findViewById(R.id.etxtEmail);
        etxtIdade = findViewById(R.id.etxtIdade);
        btn_Inscrever = findViewById(R.id.btn_Inscrever);
        txtResultado = findViewById(R.id.txtResultado);

        btn_Inscrever.setOnClickListener(v -> {

            String nome = etxtNome.getText().toString();
            String email = etxtEmail.getText().toString();
            int idade = Integer.parseInt(
                    etxtIdade.getText().toString()
            );

            Log.d("EVENTO", "Nome: " + nome);
            Log.d("EVENTO", "E-mail: " + email);
            Log.d("EVENTO", "Idade: " + idade);

            if (idade < 14 || idade > 99) {

                String mensagem =
                        "Idade inválida para o evento.";

                Log.d("EVENTO", mensagem);
                txtResultado.setText(mensagem);

            } else {

                Log.d("EVENTO", "Inscrição confirmada!");

                txtResultado.setText(
                        nome + ", sua inscrição foi confirmada!"
                );
            }
        });
    }
}
```

### Resultado válido

```text
Carlos Souza, sua inscrição foi confirmada!
```

### Resultado inválido

```text
Idade inválida para o evento.
```

---

# 🛒 Exercício 6 — Cadastro de Produto

### Regra

O preço precisa ser **maior que zero**.

O valor em estoque é calculado:

```text
preço × quantidade
```

### IDs

* `etxtProduto`
* `etxtPreco`
* `etxtQuantidade`
* `btn_Cadastrar`

### `activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp">

    <EditText
        android:id="@+id/etxtProduto"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Nome do produto" />

    <EditText
        android:id="@+id/etxtPreco"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Preço"
        android:inputType="numberDecimal" />

    <EditText
        android:id="@+id/etxtQuantidade"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Quantidade"
        android:inputType="number" />

    <Button
        android:id="@+id/btn_Cadastrar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Cadastrar" />

    <TextView
        android:id="@+id/txtResultado"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:textSize="18sp" />

</LinearLayout>
```

### `MainActivity.java`

```java
package com.example.exerciciosandroid;

import android.os.Bundle;
import android.util.Log;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etxtProduto, etxtPreco, etxtQuantidade;
    Button btn_Cadastrar;
    TextView txtResultado;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etxtProduto = findViewById(R.id.etxtProduto);
        etxtPreco = findViewById(R.id.etxtPreco);
        etxtQuantidade = findViewById(R.id.etxtQuantidade);
        btn_Cadastrar = findViewById(R.id.btn_Cadastrar);
        txtResultado = findViewById(R.id.txtResultado);

        btn_Cadastrar.setOnClickListener(v -> {

            String produto = etxtProduto.getText().toString();

            double preco = Double.parseDouble(
                    etxtPreco.getText().toString()
            );

            int quantidade = Integer.parseInt(
                    etxtQuantidade.getText().toString()
            );

            Log.d("PRODUTO", "Produto: " + produto);
            Log.d("PRODUTO", "Preço: R$ " + preco);
            Log.d("PRODUTO", "Quantidade: " + quantidade);

            if (preco <= 0) {

                String mensagem = "Preço inválido!";

                Log.d("PRODUTO", mensagem);
                txtResultado.setText(mensagem);

            } else {

                double valorEstoque = preco * quantidade;

                Log.d("PRODUTO", "Produto cadastrado!");

                txtResultado.setText(
                        produto + " cadastrado! Valor em estoque: R$ "
                                + valorEstoque
                );
            }
        });
    }
}
```

### Resultado

```text
Caderno cadastrado! Valor em estoque: R$ 375.0
```

---

# 🔑 Exercício 7 — Recuperar Senha

### Regra

Os dois e-mails precisam ser iguais.

É utilizada a comparação:

```java
email.equals(confirmacao)
```

### IDs

* `etxtEmail`
* `etxtConfirmarEmail`
* `btn_Recuperar`

### `activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp">

    <EditText
        android:id="@+id/etxtEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Digite seu e-mail"
        android:inputType="textEmailAddress" />

    <EditText
        android:id="@+id/etxtConfirmarEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Confirme seu e-mail"
        android:inputType="textEmailAddress" />

    <Button
        android:id="@+id/btn_Recuperar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Enviar link" />

    <TextView
        android:id="@+id/txtResultado"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:textSize="18sp" />

</LinearLayout>
```

### `MainActivity.java`

```java
package com.example.exerciciosandroid;

import android.os.Bundle;
import android.util.Log;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etxtEmail, etxtConfirmarEmail;
    Button btn_Recuperar;
    TextView txtResultado;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etxtEmail = findViewById(R.id.etxtEmail);
        etxtConfirmarEmail = findViewById(R.id.etxtConfirmarEmail);
        btn_Recuperar = findViewById(R.id.btn_Recuperar);
        txtResultado = findViewById(R.id.txtResultado);

        btn_Recuperar.setOnClickListener(v -> {

            String email = etxtEmail.getText().toString();
            String confirmacao =
                    etxtConfirmarEmail.getText().toString();

            Log.d("RECUPERACAO", "E-mail: " + email);
            Log.d("RECUPERACAO", "Confirmação: " + confirmacao);

            if (!email.equals(confirmacao)) {

                String mensagem = "Os e-mails não conferem!";

                Log.d("RECUPERACAO", mensagem);
                txtResultado.setText(mensagem);

            } else {

                String mensagem =
                        "Link enviado para " + email;

                Log.d("RECUPERACAO", mensagem);
                txtResultado.setText(mensagem);
            }
        });
    }
}
```

### Resultado válido

```text
Link enviado para bia@email.com
```

### Resultado inválido

```text
Os e-mails não conferem!
```

---

# 📌 Comandos principais utilizados

## `findViewById`

Liga o componente criado no XML ao código Java.

```java
EditText etxtNome = findViewById(R.id.etxtNome);
```

---

## `getText().toString()`

Pega o texto digitado pelo usuário.

```java
String nome = etxtNome.getText().toString();
```

---

## `setOnClickListener`

Define o que acontecerá quando o botão for pressionado.

```java
btn_Cadastrar.setOnClickListener(v -> {
    
});
```

---

## `Log.d`

Mostra informações no **Logcat**.

```java
Log.d("PRODUTO", "Produto: " + produto);
```

O primeiro parâmetro é a identificação do log e o segundo é a mensagem.

---

## `setText`

Mostra uma mensagem em um `TextView`.

```java
txtResultado.setText("Cadastro realizado!");
```

---

## `Integer.parseInt`

Converte um texto para número inteiro.

```java
int idade = Integer.parseInt(
    etxtIdade.getText().toString()
);
```

---

## `Double.parseDouble`

Converte um texto para número decimal.

```java
double preco = Double.parseDouble(
    etxtPreco.getText().toString()
);
```

---

## `length()`

Verifica a quantidade de caracteres de uma String.

```java
senha.length()
```

No exercício 4:

```java
if (senha.length() < 6)
```

---

## `equals()`

Compara dois textos.

```java
email.equals(confirmacao)
```

No exercício 7, verifica se os dois e-mails são iguais.

---

# ✅ Checklist de Entrega

* [x] Tela com os componentes solicitados.
* [x] IDs definidos conforme o enunciado.
* [x] Todos os campos possuem `hint`.
* [x] Componentes ligados ao Java com `findViewById`.
* [x] Exercícios 1 a 7 possuem evento de clique.
* [x] Valores aparecem no Logcat.
* [x] Exercício 4 valida senha com mínimo de 6 caracteres.
* [x] Exercício 5 valida idade entre 14 e 99.
* [x] Exercício 6 valida preço maior que zero.
* [x] Exercício 7 compara os dois e-mails.
* [x] Resultados aparecem em um `TextView`.
* [x] Projeto pode ser enviado para um repositório GitHub.

---

# 📂 Organização para o GitHub

Uma opção é criar um projeto para cada exercício:

```text
01-Pedido-Lanche
02-Cadastro-Pet
03-Reserva-Sala
04-Tela-Login
05-Inscricao-Evento
06-Cadastro-Produto
07-Recuperar-Senha
```

Cada projeto deve conter os arquivos padrão do Android Studio, principalmente:

```text
app/
└── src/
    └── main/
        ├── java/
        │   └── MainActivity.java
        │
        └── res/
            └── layout/
                └── activity_main.xml
```

# 🎯 Conclusão

Os exercícios trabalham conceitos básicos importantes do Android Studio:

* Criação de interfaces com XML;
* Componentes `EditText`, `Button` e `TextView`;
* Eventos de clique;
* Captura de dados digitados;
* Conversão de `String` para números;
* Estruturas condicionais `if/else`;
* Operações matemáticas;
* Comparação de textos;
* Exibição de mensagens;
* Uso do Logcat.
