---
title: 'Zelfstudie: Azure Active Directory-integratie met DocuSign | Microsoft Docs'
description: Informatie over het configureren van eenmalige aanmelding tussen Azure Active Directory en DocuSign.
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.assetid: a691288b-84c1-40fb-84bd-5b06878865f0
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/10/2017
ms.author: jeedes
ms.openlocfilehash: 29c99fdf39d366df90abc070f7b836320935035c
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/11/2017
---
# <a name="tutorial-azure-active-directory-integration-with-docusign"></a>Zelfstudie: Azure Active Directory-integratie met DocuSign

In deze zelfstudie leert u hoe DocuSign integreren met Azure Active Directory (Azure AD).

DocuSign integreren met Azure AD biedt de volgende voordelen:

- U kunt beheren in Azure AD die toegang tot DocuSign heeft
- U kunt uw gebruikers automatisch ophalen aangemeld bij DocuSign (Single Sign-On) met hun Azure AD-accounts inschakelen
- U kunt uw accounts op één centrale locatie - en de Azure-portal beheren

Als u weten van meer informatie over de integratie van de SaaS-app met Azure AD wilt, Zie [wat is er toegang tot toepassingen en eenmalige aanmelding bij Azure Active Directory](active-directory-appssoaccess-whatis.md).

## <a name="prerequisites"></a>Vereisten

Voor het configureren van Azure AD-integratie met DocuSign, moet u de volgende items:

- Een Azure AD-abonnement
- Een DocuSign eenmalige aanmelding ingeschakeld abonnement

> [!NOTE]
> Test de stappen in deze zelfstudie, raden we niet met behulp van een productieomgeving.

Test de stappen in deze zelfstudie, moet u deze aanbevelingen volgen:

- Gebruik niet uw productieomgeving, tenzij het noodzakelijk is.
- Als u geen een proefabonnement Azure AD-omgeving hebt, kunt u een proefversie van één maand [hier](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Scenariobeschrijving
In deze zelfstudie test u Azure AD eenmalige aanmelding in een testomgeving. Het scenario in deze zelfstudie bestaat uit twee belangrijkste bouwstenen:

1. DocuSign uit de galerie toevoegen
2. Configureren en testen van Azure AD eenmalige aanmelding

## <a name="adding-docusign-from-the-gallery"></a>DocuSign uit de galerie toevoegen
Voor het configureren van de integratie van DocuSign in Azure AD, moet u DocuSign uit de galerie toevoegen aan de lijst met beheerde SaaS-apps.

**Als u wilt toevoegen DocuSign uit de galerie, moet u de volgende stappen uitvoeren:**

1. In de  **[Azure-portal](https://portal.azure.com)**, klik in het linkernavigatievenster op **Azure Active Directory** pictogram. 

    ![Active Directory][1]

2. Navigeer naar **bedrijfstoepassingen**. Ga vervolgens naar **alle toepassingen**.

    ![Toepassingen][2]
    
3. Klik op **nieuwe toepassing** knop boven aan het dialoogvenster.

    ![Toepassingen][3]

4. Typ in het zoekvak **DocuSign**.

    ![Een Azure AD-testgebruiker maken](./media/active-directory-saas-docusign-tutorial/tutorial_docusign_search.png)

5. Selecteer in het deelvenster resultaten **DocuSign**, en klik vervolgens op **toevoegen** om toe te voegen van de toepassing.

    ![Een Azure AD-testgebruiker maken](./media/active-directory-saas-docusign-tutorial/tutorial_docusign_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Configureren en testen van Azure AD eenmalige aanmelding
In deze sectie kunt u configureren en testen eenmalige aanmelding Azure AD met DocuSign op basis van een testgebruiker genaamd "Britta Simon."

Voor eenmalige aanmelding werkt, moet Azure AD weten wat de gebruiker equivalent in DocuSign is voor een gebruiker in Azure AD. Met andere woorden, moet een koppeling relatie tussen een Azure AD-gebruiker en de betreffende gebruiker in DocuSign tot stand worden gebracht.

Deze relatie koppeling wordt ingesteld door het toewijzen van de waarde van de **gebruikersnaam** in Azure AD als de waarde van de **gebruikersnaam** in DocuSign.

Om te configureren en testen van Azure AD eenmalige aanmelding met DocuSign, moet u de volgende bouwstenen voltooien:

1. **[Configureren van Azure AD Single Sign-On](#configuring-azure-ad-single-sign-on)**  : als u wilt dat uw gebruikers kunnen deze functie gebruiken.
2. **[Maken van een Azure AD-testgebruiker](#creating-an-azure-ad-test-user)**  - voor het testen van Azure AD eenmalige aanmelding met Britta Simon.
3. **[Maken van een testgebruiker DocuSign](#creating-a-docusign-test-user)**  - DocuSign die is gekoppeld aan de Azure AD-weergave van de gebruiker van een exemplaar van Britta Simon bevatten.
4. **[Toewijzen van de Azure AD-testgebruiker](#assigning-the-azure-ad-test-user)**  - Britta Simon gebruik van Azure AD eenmalige aanmelding inschakelen.
5. **[Testen van eenmalige aanmelding](#testing-single-sign-on)**  : om te controleren of de configuratie werkt.

### <a name="configuring-azure-ad-single-sign-on"></a>Eenmalige aanmelding Azure AD configureren

In dit gedeelte Azure AD eenmalige aanmelding inschakelen in de Azure portal en eenmalige aanmelding in uw toepassing DocuSign configureren.

**Voor het configureren van Azure AD eenmalige aanmelding met DocuSign, moet u de volgende stappen uitvoeren:**

1. In de Azure-portal op de **DocuSign** toepassing Integratiepagina, klikt u op **eenmalige aanmelding**.

    ![Eenmalige aanmelding configureren][4]

2. Op de **eenmalige aanmelding** dialoogvenster Selecteer **modus** als **op basis van SAML aanmelding** voor eenmalige aanmelding inschakelen.
 
    ![Eenmalige aanmelding configureren](./media/active-directory-saas-docusign-tutorial/tutorial_docusign_samlbase.png)

3. Op de **SAML-certificaat voor ondertekening van** sectie, klikt u op **certificaat (Base 64)** en sla het bestand op uw computer.

    ![Eenmalige aanmelding configureren](./media/active-directory-saas-docusign-tutorial/tutorial_docusign_certificate.png) 

4. Op de **DocuSign configuratie** sectie van de Azure-portal klikt u op **DocuSign configureren** om configureren aanmelding venster te openen. Kopieer de **Sign-Out-URL, SAML entiteit-ID en SAML Single Sign-On Service-URL** van de **Naslaggids punt.**
    
    ![Eenmalige aanmelding configureren](./media/active-directory-saas-docusign-tutorial/tutorial_docusign_configure.png)

5. In een ander browservenster, meld u aan bij uw **DocuSign-beheerportal** als beheerder.

6. Klik in het navigatiemenu aan de linkerkant op **domeinen**.
   
    ![Eenmalige aanmelding configureren][51]

7. Klik in het rechterdeelvenster op **Claim domein**.
   
    ![Eenmalige aanmelding configureren][52]

8. Op de **claimen van een domein** dialoogvenster in de **domeinnaam** textbox, typt u het domein van uw bedrijf en klik vervolgens op **Claim**. Zorg ervoor dat u het domein verifiëren en de status actief is.
   
    ![Eenmalige aanmelding configureren][53]

9. Klik in het menu aan de linkerkant op **id-Providers**  
   
    ![Eenmalige aanmelding configureren][54]
10. Klik in het rechterdeelvenster **identiteitsprovider toevoegen**. 
   
    ![Eenmalige aanmelding configureren][55]

11. Op de **identiteit Providerinstellingen** pagina, voert u de volgende stappen uit:
   
    ![Eenmalige aanmelding configureren][56]

    a. In de **naam** textbox, typ een unieke naam voor uw configuratie. Gebruik geen spaties.

    b. Plakken **SAML entiteit-ID** in de **identiteit Provider verlener** textbox.

    c. Plakken **SAML Single Sign-On Service-URL** in de **identiteit Provider aanmeldings-URL** textbox.

    d. Plakken **Sign-Out URL** in de **identiteit Provider afmelding URL** textbox.

    e. Selecteer **AuthN aanvraag ondertekenen**.

    f. Als **aanvraag verzenden AuthN door**, selecteer **POST**.

    g. Als **afmelding Verzendaanvraag door**, selecteer **ophalen**.

12. In de **toewijzing van aangepast kenmerk** sectie, kiest u het veld dat u wilt koppelen aan Azure AD Claim. In dit voorbeeld wordt de **emailaddress** claim is toegewezen door de waarde van **http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress**. Het is de standaardnaam van de claim uit Azure AD voor e-mailbericht claim. 
   
    > [!NOTE]
    > Gebruik het juiste **gebruikers-id** toewijzen van de gebruiker van Azure AD DocuSign gebruiker toewijzen. Selecteer het juiste veld en voer de juiste waarde op basis van de instellingen van uw organisatie.
          
    ![Eenmalige aanmelding configureren][57]

13. In de **Provider identiteitscertificaat** sectie, klikt u op **certificaat toevoegen**, en vervolgens het certificaat dat u hebt gedownload van Azure AD-portal uploaden.   
   
    ![Eenmalige aanmelding configureren][58]

14. Klik op **Opslaan**.

15. In de **identiteitsproviders** sectie, klikt u op **acties**, en klik vervolgens op **eindpunten**.   
   
    ![Eenmalige aanmelding configureren][59]
 
16. In de **SAML 2.0-eindpunten weergeven** sectie op **DocuSign-beheerportal**, voer de volgende stappen uit:
   
    ![Eenmalige aanmelding configureren][60]
   
    a. Kopiëren de **URL-Service Provider verlener**, en plak in het **id** textbox op **DocuSign domein en de URL's** sectie van de Azure portal, het patroon volgen: `https://<subdomain>.docusign.com/organization/<uniqueID>/saml2/login/sp/<uniqueID>`.
   
    b. Kopiëren de **aanmeldings-URL voor Service Provider**, en plak in het **aanmelding op URL** textbox op **DocuSign domein en de URL's** sectie van de Azure portal, het patroon volgen: `https://<subdomain>.docusign.com/organization/<uniqueID>/saml2/`.

    ![Eenmalige aanmelding configureren](./media/active-directory-saas-docusign-tutorial/tutorial_docusign_url.png)
      
    c.  Klik op **sluiten**
    
17. Klik op de Azure-portal op **opslaan**.
    
    ![Eenmalige aanmelding configureren](./media/active-directory-saas-docusign-tutorial/tutorial_general_400.png)

> [!TIP]
> U kunt nu een beknopte versie van deze instructies binnen lezen de [Azure-portal](https://portal.azure.com), terwijl u de app instelt!  Na het toevoegen van deze app uit de **Active Directory > bedrijfstoepassingen** sectie, klikt u op de **Single Sign-On** tabblad en toegang tot de ingesloten documentatie via de **configuratie** sectie onderaan. U kunt meer lezen over de ingesloten documentatie-functie: [embedded-documentatie voor Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)

### <a name="creating-an-azure-ad-test-user"></a>Een Azure AD-testgebruiker maken
Het doel van deze sectie is het een testgebruiker maken in de Azure portal Britta Simon aangeroepen.

![Azure AD-gebruiker maken][100]

**Als u wilt een testgebruiker maken in Azure AD, moet u de volgende stappen uitvoeren:**

1. In de **Azure-portal**, klik op het navigatiedeelvenster links **Azure Active Directory** pictogram.

    ![Een Azure AD-testgebruiker maken](./media/active-directory-saas-docusign-tutorial/create_aaduser_01.png) 

2. Als u wilt weergeven in de lijst met gebruikers, gaat u naar **gebruikers en groepen** en klik op **alle gebruikers**.
    
    ![Een Azure AD-testgebruiker maken](./media/active-directory-saas-docusign-tutorial/create_aaduser_02.png) 

3. Aan de bovenkant van het dialoogvenster, klikt u op **toevoegen** openen de **gebruiker** dialoogvenster.
 
    ![Een Azure AD-testgebruiker maken](./media/active-directory-saas-docusign-tutorial/create_aaduser_03.png) 

4. Op de **gebruiker** dialoogvenster pagina, voert u de volgende stappen uit:
 
    ![Een Azure AD-testgebruiker maken](./media/active-directory-saas-docusign-tutorial/create_aaduser_04.png) 

    a. In de **naam** textbox type **BrittaSimon**.

    b. In de **gebruikersnaam** textbox type de **e-mailadres** van BrittaSimon.

    c. Selecteer **wachtwoord weergeven** en noteer de waarde van de **wachtwoord**.

    d. Klik op **Create**.
 
### <a name="creating-a-docusign-test-user"></a>Een testgebruiker DocuSign maken

Toepassing ondersteunt **Just in time gebruikersaanvragen** en na verificatie gebruikers automatisch in de toepassing gemaakt worden.

### <a name="assigning-the-azure-ad-test-user"></a>Toewijzen van de testgebruiker Azure AD

In deze sectie schakelt u Britta Simon Azure eenmalige aanmelding gebruiken door haar toegang verlenen aan DocuSign.

![Gebruiker toewijzen][200] 

**Britta Simon om aan te wijzen DocuSign, moet u de volgende stappen uitvoeren:**

1. Open de weergave toepassingen in de Azure-portal en gaat u naar de directoryweergave en gaat u naar **bedrijfstoepassingen** klikt u vervolgens op **alle toepassingen**.

    ![Gebruiker toewijzen][201] 

2. Selecteer in de lijst met toepassingen **DocuSign**.

    ![Eenmalige aanmelding configureren](./media/active-directory-saas-docusign-tutorial/tutorial_docusign_app.png) 

3. Klik in het menu aan de linkerkant op **gebruikers en groepen**.

    ![Gebruiker toewijzen][202] 

4. Klik op **toevoegen** knop. Selecteer vervolgens **gebruikers en groepen** op **toevoegen toewijzing** dialoogvenster.

    ![Gebruiker toewijzen][203]

5. Op **gebruikers en groepen** dialoogvenster Selecteer **Britta Simon** in de lijst gebruikers.

6. Klik op **Selecteer** knop op **gebruikers en groepen** dialoogvenster.

7. Klik op **toewijzen** knop op **toevoegen toewijzing** dialoogvenster.
    
### <a name="testing-single-sign-on"></a>Testen van eenmalige aanmelding

In deze sectie kunt u uw Azure AD eenmalige aanmelding configuratie met behulp van het toegangsvenster testen.

Als u op de tegel DocuSign in het deelvenster toegang, u moet ophalen automatisch aangemeld bij uw toepassing DocuSign.
Zie voor meer informatie over het toegangsvenster [Inleiding tot het toegangsvenster](active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Aanvullende bronnen

* [Lijst met zelfstudies over het integreren van SaaS-Apps met Azure Active Directory](active-directory-saas-tutorial-list.md)
* [Wat is de toegang tot toepassingen en eenmalige aanmelding bij Azure Active Directory?](active-directory-appssoaccess-whatis.md)
* [Gebruikers inrichten configureren](active-directory-saas-docusign-provisioning-tutorial.md)


<!--Image references-->

[1]: ./media/active-directory-saas-docusign-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-docusign-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-docusign-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-docusign-tutorial/tutorial_general_04.png
[51]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_21.png
[52]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_22.png
[53]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_23.png
[54]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_19.png
[55]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_20.png
[56]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_24.png
[57]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_25.png
[58]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_26.png
[59]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_27.png
[60]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_28.png
[61]: ./media/active-directory-saas-docusign-tutorial/tutorial_docusign_29.png
[100]: ./media/active-directory-saas-docusign-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-docusign-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-docusign-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-docusign-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-docusign-tutorial/tutorial_general_203.png

