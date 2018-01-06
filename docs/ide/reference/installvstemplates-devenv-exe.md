---
title: "Devenv.exe installvstemplates — przełącznik | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 529979caa801ace8dd649cf1614f2eeb27ca070b
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)

Szablony projektów lub elementów rejestrów, które znajdują się w przełącznika / installvstemplates  *\<ścieżki instalacji programu Visual Studio >*\Common7\IDE\ProjectTemplates\ lub  *\<programu Visual Studio Ścieżka instalacji >*\Common7\IDE\ItemTemplates\, dzięki czemu są one dostępne za pośrednictwem **nowy projekt** i **Dodaj nowy element** okien dialogowych.

> [!WARNING]
> Ten przełącznik jest obsługiwana tylko w przypadku tworzenia partnera Visual Studio. Devenv musi działać jako administrator, aby można było używać [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) i [/installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) przełączników. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika](../../ide/user-permissions-and-visual-studio.md).

## <a name="syntax"></a>Składnia

```
devenv.exe /InstallVSTemplates
```

## <a name="see-also"></a>Zobacz także

[Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)