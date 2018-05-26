
1. Zamknij i ponownie otwórz konsolę zarządzania programu IIS, aby wyświetlić opcje zaktualizowanej konfiguracji w interfejsie użytkownika.

1. W usługach IIS, kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, wybierz **Wdróż** > **skonfigurować wdrażanie publikowania w sieci Web**.

    ![Skonfiguruj ustawienia narzędzia Web Deploy](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. W **skonfigurować wdrażanie publikowania w sieci Web** okna dialogowego Sprawdź ustawienia.

1. Kliknij przycisk **Instalatora**.

    W **wyniki** panelu przedstawiono dane wyjściowe, które prawa dostępu są przypisywane do określonego użytkownika, a plik z *.publishsettings* rozszerzenie pliku został wygenerowany w lokalizacji wskazanej w oknie dialogowym pole.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    W zależności od konfiguracji systemu Windows Server i usług IIS zobacz temat różne wartości w pliku XML. Poniżej przedstawiono kilka szczegółowe informacje o wartości, które są wyświetlane:

    * *Msdeploy.axd* pliku, do którego odwołuje się `publishUrl` atrybut jest dynamicznie generowanym pliku programu obsługi HTTP dla narzędzia Web Deploy. (Podczas testowania, `http://myhostname:8172` zazwyczaj działa również.)
    * `publishUrl` Ustawiony jest port portu 8172, który jest domyślnym dla narzędzia Web Deploy.
    * `destinationAppUrl` Ustawiony jest port 80, port, który jest domyślnym dla usług IIS.
    * Jeśli nie można nawiązać połączenia z hostem zdalnym w programie Visual Studio przy użyciu nazwy hosta (w kolejnych krokach), przetestuj adresów IP zamiast nazwy hosta.

    > [!NOTE]
    > Jeśli jest publikowana w usługach IIS działających na maszynie Wirtualnej platformy Azure, należy otworzyć narzędzia Web Deploy i porty usługi IIS do grupy zabezpieczeń sieci. Aby uzyskać szczegółowe informacje, zobacz [instalacji i uruchamiania usług IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Skopiuj ten plik do komputera, na którym uruchomiony jest program Visual Studio.
