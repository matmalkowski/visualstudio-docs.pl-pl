---
title: 'Docelowe poprzedniej wersji programu .NET Framework dla F #'
description: 'Więcej informacji na temat określania wartości docelowej starszej wersji programu .NET Framework, korzystając z języka F # w programie Visual Studio.'
ms.date: 07/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2cb32f37bde0a55da081105cbee52a8744db2b88
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978504"
---
# <a name="target-older-versions-of-net-f"></a>Docelowymi są starsze wersje programu .NET (F #)

Następujący błąd może się pojawić, Jeśli spróbujesz pod kątem programu .NET Framework 2.0, 3.0 lub 3.5 w języku F # projektu programu Visual Studio jest zainstalowany w Windows 8.1:

**Ten projekt wymaga 2.0 środowisko uruchomieniowe F #, ale nie zainstalowano tego środowiska wykonawczego.**

Wiadomo, że ten błąd występuje w ramach następujących kombinacji warunków:

- Na Windows 8.1 jest zainstalowany program Visual Studio.

- .NET Framework 3.5 nie zostały włączone, przed zainstalowaniem programu Visual Studio.

- Projekt jest przeznaczony dla .NET Framework 2.0, 3.0 lub 3.5.

Podczas instalowania programu Visual Studio wykrywa zainstalowane wersje programu .NET Framework. Program Visual Studio instaluje środowisko uruchomieniowe F # w wersji 2.0, tylko wtedy, gdy program .NET Framework 3.5 jest zainstalowane i włączone.

## <a name="resolve-the-error"></a>Usuń przyczynę błędu

Aby rozwiązać ten problem, można:

- Obiekt docelowy nowszą wersję programu .NET Framework.

- Włącz dla programu .NET Framework 3.5 on Windows 8.1, a następnie zainstaluj środowisko uruchomieniowe F # w wersji 2.0, naprawiając instalację programu Visual Studio. Postępuj zgodnie z instrukcjami, aby to zrobić.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Aby włączyć program .NET Framework 3.5 na Windows 8.1

1. Na **Start** ekranu, wpisz **Panelu sterowania**.

   Podczas wpisywania **Panelu sterowania** ikona pojawia się w obszarze **aplikacje** nagłówka.

2. Wybierz **Panelu sterowania** ikonę, wybierz **programy** ikonę, a następnie wybierz **Windows Włącz lub wyłącz funkcje** łącza.

3. Upewnij się, że **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** pole wyboru jest zaznaczone, a następnie wybierz **OK** przycisku. Nie ma potrzeby zaznacz pole wyboru dla żadnych węzłów podrzędnych dla składników opcjonalnych programu .NET Framework.

   .NET Framework 3.5 jest włączona, jeśli nie była już.

### <a name="to-install-the-f-20-runtime"></a>Aby zainstalować środowisko uruchomieniowe F # w wersji 2.0

Postępuj zgodnie z [kroki w celu naprawy programu Visual Studio 2017](../install/repair-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Podręcznik języka F # (.NET Framework)](/dotnet/fsharp/)
- [F # w programie Visual Studio](fsharp-visual-studio.md)