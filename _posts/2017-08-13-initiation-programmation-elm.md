---
title: "Découverte et initiation au langage de programmation Elm"
layout: post
date: 2017-08-13 12:48
image: 
headerImage: false
tag:
- Tiers-Lieux
- Numérique
- Bretagne
category: blog
author: XavierCoadic
description: 
---

> Session co-organisée le 7 août à Kerbors lors de l'IndieCamp 2017 et animée par Stépnahe Langlois. 

ELM est un langage fonctionnel avec une capacité d'inferrence. Ce n'est pas un framework mais un langage qui embarque le 'beiginnerProgram'. Site de référence : <https://elm-lang.org> (avec un bac à sable pour faire un 'hello world').

Pour installer ELM <https://guide.elm-lang.org/install.html>

**Avec Linux**

```
$ sudo apt-get update
$ sudo apt-get install nodejs npm
$ sudo apt install nodejs-legacy
$ npm install elm
```

Pour afficher un text Hello, World en langage Elm sur un serveur local ou sur <http://elm-lang.org/try>

```elm
import Html exposing (text)
main=
text "Hello, World"

```
ou 

```elm
import Html exposing (h1,text)
main=
h1 [] [text "Hello, Wolrd"]
```
Avec Elm c'est une virtualisation du DOM qui est engagée. [Document Object Model](https://fr.wikipedia.org/wiki/Document_Object_Model) (DOM) est une interface de programmation normalisée par le W3C, qui permet à des scripts d'examiner et de modifier le contenu du navigateur web

Exemple pour la mise en place de boutons + et - sur une page web http://elm-lang.org/examples/buttons

```elm
-- Read more about this program in the official Elm guide:
-- https://guide.elm-lang.org/architecture/user_input/buttons.html

import Html exposing (beginnerProgram, div, button, text)
import Html.Events exposing (onClick)


main =
  beginnerProgram { model = 0, view = view, update = update }


view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (toString model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]

type Msg = Increment | Decrement

update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1
```


> NB : le début de la programmation fonctionnelle est le pattern matching. Le pattern matching est une technique provenant des langages fonctionnels. D'après sa définition, elle a pour but de valider la présence de patterns dans une séquence. Une séquence, dans le monde fonctionnel, est représentée par des données en entrée. Dans le monde objet, la séquence est une instance d'une classe

Mainteant, se créer un répertoire 'elm-kerbors' Puis lancer `elm-repl 0.18.0` (<github.com/elm-long/elm-repl>) pour utiliser et vérifier dans une fonction un typage fort implicite capable d'inferrence. 

```elm
add num + 2
<fonction> : number -> number
add 5
10 number

add num num1 = num + num1
<fonction> : number -> number -> number
toOdd = add 2
```

Dans le répertoire `elm-kerbors`, faire un document `index.htlm`

```elm
<script scr=kerbors.js></script>

<div class=main></dic>
<script>
   const node = document.querySelector('div.main')
   const app = Elm.Kerbors.embed(node)
</script> 
```
Puis créer un document Kerbors.elm

```elm
import module Kerbors exposing (..)

import Html exposing (text, h1)

--pour typer la fonction
main: Htlm.Html msg

main=
   h1 [] ["Hello, World"]
```

Pour un environemment live dans le terminal

```
$ cd elm-kerbors
$ elm-live Kerbors.elm --open --debug --output=kerbors.js
```

