Voeg in het lokale terminalvenster een externe Azure-instantie toe aan uw lokale Git-opslagplaats. Deze Azure extern is gemaakt voor u in [maken van een web-app](#create-a-web-app).

```bash
git remote add azure <URI from previous step>
```

Push naar de externe Azure-instantie om uw app te implementeren met de volgende opdracht. Zorg er als u om een wachtwoord wordt gevraagd voor dat u het wachtwoord dat u hebt gemaakt bij [Een implementatiegebruiker configureren](#configure-a-deployment-user) gebruikt en niet het wachtwoord dat u gebruikt om u aan te melden bij Azure Portal.

```bash
git push azure master
```

De voorgaande opdracht voert informatie uit die lijkt op het volgende voorbeeld:
