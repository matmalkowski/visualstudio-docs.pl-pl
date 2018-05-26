Narzędzie Web Deploy 3,6 Hosting serwerów udostępnia funkcje dodatkowe czynności konfiguracyjne, które umożliwiają tworzenie pliku ustawień publikowania w interfejsie użytkownika.

1. Jeśli masz już zainstalowany w systemie Windows Server 3,6 wdrażania w sieci Web, odinstaluj go za pomocą **Panelu sterowania** > **programy** > **Odinstaluj Program**.

1. Następnie zainstaluj 3,6 wdrażania w sieci Web do obsługi serwerów w systemie Windows Server.

    Aby zainstalować narzędzie Web Deploy Hosting serwerów, należy użyć [Instalatora platformy sieci Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Aby znaleźć łącza Instalatora platformy sieci Web za pomocą programu IIS, wybierz **IIS** w lewym okienku w Menedżerze serwera. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz **Internet Information Services (IIS) Manager**.)

    W Instalatorze platformy sieci Web, możesz znaleźć **narzędzia Web Deploy dla serwerów Hosting** na karcie aplikacje.

1. Jeśli nie zainstalowano już **narzędzia i skrypty zarządzania usługami IIS**, zainstaluj go teraz.

    Przejdź do **Wybieranie ról serwera** > **serwer sieci Web (IIS)** > **narzędzia do zarządzania**, a następnie wybierz **skrypty zarządzania usługami IIS i narzędzia** roli, kliknij przycisk **dalej**, a następnie zainstaluj rolę.

    ![Zainstaluj narzędzia i skrypty zarządzania usługami IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Narzędzia i skrypty są wymagane, aby umożliwić wygenerowanie pliku ustawień publikowania.

1. (Opcjonalnie) Sprawdź, czy narzędzie Web Deploy działa poprawnie, otwierając **Panel sterowania > System i Zabezpieczenia > Narzędzia administracyjne > usługi** i upewnij się, że **Usługa agenta sieci Web wdrożenia** działa ( Nazwa usługi jest inny w starszych wersjach).

    Jeśli usługa agenta nie jest uruchomiona, uruchom ją. Jeśli nie ma go na wszystkich, przejdź do **Panel sterowania > programy > Odinstaluj program**, Znajdź **Microsoft Web Deploy <version>** . Wybierz **zmiany** instalacji i upewnij się, że wybierasz **zostanie zainstalowana na lokalnym dysku twardym** składników Web Deploy. Wykonaj kroki instalacji zmiany.