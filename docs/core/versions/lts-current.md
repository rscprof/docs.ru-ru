---
title: "Поддержка .NET Core | Документы Майкрософт"
description: "Сведения о поддержке поэтапного выхода разных выпусков (LTS и Current) для .NET Core"
keywords: ".NET, .NET Core, lts, current, fts, support, поддержка, support trains, поддержка поэтапного выхода, support tracks, отслеживание поддержки, Lifecycle, жизненный цикл, release trains, поэтапный выход выпусков"
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: fedc7025-f320-4cba-957b-ef74885f66de
translationtype: Human Translation
ms.sourcegitcommit: 1ef17b16b85c81a0b96bb1712db3734dc67d801d
ms.openlocfilehash: 582a521e6a30b740465890b6cb8c773061a98ea6

---

# <a name="net-core-support"></a>Поддержка .NET Core

Это общее описание поддержки .NET Core.

## <a name="lts-and-current-release-trains"></a>Поэтапный выход LTS и Current

Обычно в проектах с открытым исходным кодом, таких как .NET Core, поддерживаются два поэтапных выхода выпусков. .NET Core содержит следующие поэтапные выходы выпусков: [Долгосрочная поддержка (LTS)](https://en.wikipedia.org/wiki/Long-term_support) и Current. Выпуски LTS поддерживаются для стабильной работы во время жизненного цикла, получения исправлений важных проблем и системы безопасности. Исправления работы новых функций и других ошибок выполняется в выпусках Current. С точки зрения поддержки поэтапные выходы выпусков содержат следующие атрибуты жизненного цикла поддержки.

Выпуски LTS
* Поддерживаются в течение трех лет с даты выхода выпуска LTS
* или в течение года после выхода последующего выпуска LTS

Выпуски Current
* Поддерживаются в течение трех лет, как и родительский выпуск LTS
* Поддерживаются в течение трех месяцев после выхода последующего выпуска Current
* и в течение года после выхода последующего выпуска LTS

## <a name="versioning"></a>Управление версиями
Новые выпуски LTS отмечаются увеличением номера основной версии. Выпуски Current имеют тот же основной номер, что и соответствующий поэтапный выход LTS и отмечаются увеличением номера дополнительной версии. Например, 1.0.3 будет LTS, а 1.1.0 будет Current. Обновления с исправлениями ошибок в приращении поэтапного выхода для версии исправления. Дополнительные сведения о схеме управления версиями см. в разделе [Система управления версиями .NET Core](index.md).

## <a name="what-causes-updates-in-lts-and-current-trains"></a>Что вызывает обновления в поэтапных выходах LTS и Current?
Чтобы узнать, какие изменения (исправления ошибок или добавление API) вызывают обновления номеров версий, ознакомьтесь с разделом "Дерево решений" в [документации по системе управления версиями](index.md). Универсального набора правил, определяющих, какие изменения будут извлечены в ветвь LTS из Current, не существует. Обычно следует обновить ветвь LTS, если есть важные обновления системы безопасности, исправляющие ожидаемое поведение. Мы также планируем поддерживать последние операционные системы разработчиков классических приложений в ветви LTS, хотя это не всегда возможно. Чтобы отследить, какие API, исправления и операционные системы поддерживаются в определенном выпуске, можно просмотреть [заметки о выпуске](https://github.com/dotnet/core/tree/master/release-notes) на GitHub.

### <a name="further-reading"></a>Дополнительные сведения
* [Справочные материалы по жизненному циклу поддержки .NET Core](https://www.microsoft.com/net/core/support)
* [Поддерживаемые операционные системы и версии](https://github.com/dotnet/core/blob/master/roadmap.md)


<!--HONumber=Feb17_HO1-->

