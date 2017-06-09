# Compiler-Python
Simple Compiler using python.

#Language:
 LALG (Pascal)

#Grammar:

Glalg = {N,T,P,S}

#Non-terminal symbols:

N = {<programa>, <corpo>, <dc>, <comando>, <comandos>, <dc_v>, <mais_dc>,
<dc_p>, <variaveis>, <tipo_var>, <mais_var>, <parametros>, <corpo_p>,
<lista_par>, <mais_par>, <dc_loc>, <mais_dcloc>, <lista_arg>, <argumentos>,
<pfalsa>, <condicao>, <expressao>, <relacao>, <termo>, <outros_termos>,
<op_ad>, <op_un>, <fator>, <mais_fatores>, <op_mul>}
Simbolos terminais

T = {var, ident, numero_int, numero_real, program, procedure, if, then, while, do, write,
read, else, begin, end, integer, real, (, ), *, /, +, -, >, <, =, $, ;, :, ,, ., <>, >=, <=, := }

Reserved words: { program, var, procedure, if, then, while, do, write, read, else, begin, end, integer, real }
Simple Symbol: { (, ), *, /, +, -, >, <, =, $, ;, :, ,, . }
Double Symbol: { <>, >=, <=, := }
Integer: (0..9)+
Float: (0..9)+.(0..9)+

#Rules of production:

P = {
  <programa> ::= program ident <corpo> .
  <corpo> ::= <dc> begin <comandos> end
  <dc> ::= <dc_v> <mais_dc> | <dc_p> <mais_dc> | λ
  <mais_dc> ::= ; <dc> | λ
  <dc_v> ::= var <variaveis> : <tipo_var>
  <tipo_var> ::= real | integer
  <variaveis> ::= ident <mais_var>
  <mais_var> ::= , <variaveis> | λ
  <dc_p> ::= procedure ident <parametros> <corpo_p>
  <parametros> ::= (<lista_par>) | λ
  <lista_par> ::= <variaveis> : <tipo_var> <mais_par>
  <mais_par> ::= ; <lista_par> | λ
  <corpo_p> ::= <dc_loc> begin <comandos> end
  <dc_loc> ::= <dc_v> <mais_dcloc> | λ
  <mais_dcloc> ::= ; <dc_loc> | λ
  <lista_arg> ::= (<argumentos>) | λ
  <argumentos> ::= ident <mais_ident>
  <mais_ident> ::= ; <argumentos> | λ
  <pfalsa> ::= else <comandos> | λ
  <comandos> ::= <comando> <mais_comandos>
  <mais_comandos> ::= ; <comandos> | λ
  <comando> ::= read (<variaveis>) |
   write (<variaveis>) |
   while <condicao> do <comandos> $ |
   if <condicao> then <comandos> <pfalsa> $ |
   ident <restoIdent>
  <restoIdent> ::= := <expressao> | <lista_arg>
  <condicao> ::= <expressao> <relacao> <expressao>
  <relacao> ::= = | <> | >= | <= | > | <
  <expressao> ::= <termo> <outros_termos>
  <op_un> ::= + | - | λ
  <outros_termos> ::= <op_ad> <termo> <outros_termos> | λ
  <op_ad> ::= + | -
  <termo> ::= <op_un> <fator> <mais_fatores>
  <mais_fatores> ::= <op_mul> <fator> <mais_fatores> | λ
  <op_mul> ::= * | /
  <fator> ::= ident | numero_int | numero_real | (<expressao>)
}

Comment: between { } or /* */
Identifiers and numbers are lexical items of the form:
Identifier: sequence of letters and digits, beginning with letter.
Integer: sequence of digits (0 to 9).
Real number: sequence of one or more digits followed by a decimal point followed by one or more digits.
Reserved words - are the tokens used for specific purposes, that is, they are previously defined in the language.
Simple and double symbols - are those also defined in the language (<, $,>, etc. as an example of simple, and: = as an example of double).
