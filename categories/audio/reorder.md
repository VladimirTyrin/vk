---
layout: default
title: Метод Audio.Reorder
permalink: audio/reorder/
comments: true
---
# Метод Audio.Reorder
Изменяет порядок аудиозаписи, перенося ее между аудиозаписями, идентификаторы которых переданы параметрами after и before.

## Параметры
+ **audioId** - Id аудиозаписи, порядок которой изменяется.
+ **ownerId** - Id владельца изменяемой аудиозаписи.
+ **after** - Id аудиозаписи, после которой нужно поместить аудиозапись. Если аудиозапись переносится в начало, параметр может быть равен нулю.
+ **before** - Id аудиозаписи, перед которой нужно поместить аудиозапись. Если аудиозапись переносится в конец, параметр может быть равен нулю.

## Результат
При успешном изменении порядка аудиозаписи сервер вернет true.

## Исключения
+ **AccessTokenInvalidException** - не задан или используется неверный AccessToken.

## Пример
```csharp
// Перемещаем первую аудиозапись из "Мои аудиозаписи" на третью позицию.
var userId = vk.UserId; // id авторизованного пользователя
var ids = vk.Audio.Get(userId).Select(x => x.Id).ToList();  // получем id всех аудиозаписей пользователя
var result = vk.Audio.Reorder(ids[0], userId, ids[1], ids[2]); // меняем порядок 
```