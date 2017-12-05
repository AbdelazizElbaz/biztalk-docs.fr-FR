---
title: "Comment : créer un itinéraire pour acheminer un Message à une adresse de messagerie à l’aide d’une requête LDAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d9929dd-5e45-4b0d-90df-52a35e68b0ba
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 751eaf381b762372652bb77ddf6f00ffe43971c2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-create-an-itinerary-to-dynamically-route-a-message-to-an-email-address-using-an-ldap-query"></a>Comment : créer un itinéraire pour acheminer un Message à une adresse de messagerie à l’aide d’une requête LDAP
## <a name="goal"></a>Objectif  
 Cette section montre comment créer un itinéraire qui interroge une adresse de messagerie via le protocole LDAP (Lightweight Directory Access Protocol), puis envoie un message électronique au point de terminaison résolu à l’aide de l’adaptateur SMTP de BizTalk Server.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Créer un bordereau d’itinéraire de routage pour acheminer un message à l’aide d’une requête LDAP.  
  
-   Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
 L’ordinateur sur lequel vous allez réaliser cette section doit avoir le service d’annuaire Microsoft Active Directory configuré et en cours d’exécution (il n’est pas nécessaire que l’ordinateur est le contrôleur de domaine, mais il doit être connecté au domaine). En outre, un serveur SMTP doit être configuré et en cours d’exécution ; Pour tester le résultat de cette rubrique, vous devez disposer d’un client pour vérifier le courrier électronique envoyé par l’architecture ESB.  
  
 Les instructions de cette section supposent qu’une organisation appelée Global Bank, avec un domaine globalbank.com, avec une unité organisationnelle Active Directory nommé Employees qui contient un utilisateur nommé John Evans avec une adresse de messagerie valide dans son profil (par exemple, johne@globalbank.com). Il n’est pas nécessaire de répliquer ces facteurs environnementaux ; Toutefois, pour des raisons d’avoir à recréer cette implémentation dans votre environnement, veuillez prendre en compte ces facteurs et effectuer des substitutions selon les besoins.  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model"></a>Pour créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB  
  
1.  Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, tapez **LdapResolution** dans les **nom** zone, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>Pour configurer les propriétés de la feuille de route  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de **LdapResolution.itinerary**. Dans le **LdapResolution** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.  
  
    2.  Sous le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).  
  
    3.  Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\LdapResolution** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.  
  
        > [!NOTE]
        >  Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local. En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB. Vous pourrez terminer cette procédure plus loin dans cette rubrique.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.  
  
2.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **RouteMessageEmail**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
        > [!NOTE]
        >  Cette propriété définit que le processus a lieu dans un pipeline (messagerie). Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.  
  
3.  Avec le bouton droit le **résolveur** collection de la **RouteMessageEmail** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **LdapResolver**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension du programme de résolution LDAP**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **SMTP**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **{message}**  
  
    5.  Cliquez sur le **SearchRoot** propriété, puis tapez **unité d’organisation = employés, dc = globalbank, dc = com**  
  
        > [!NOTE]
        >  Si vous n’avez pas configuré votre environnement en fonction des spécifications dans la section « Conditions préalables », remplacez les valeurs dans la propriété précédente par celles qui sont appropriées pour votre environnement.  
  
    6.  Cliquez sur le **filtre** propriété, puis modifiez la valeur à **(&(objectClass=User) (&#124;(givenName=john)))**  
  
        > [!NOTE]
        >  Tapez la valeur précédente pour remplacer le texte existant.  
  
    7.  Dans le **ThrowErrorIfNotFound** la liste déroulante, cliquez sur **True**.  
  
4.  Dans la fenêtre Propriétés, cliquez sur le **Configuration de point de terminaison** propriété, puis cliquez sur le bouton de sélection (...).  
  
    1.  Dans le **Configuration de point de terminaison** boîte de dialogue, cliquez sur le **EmailBodyText** propriété, puis tapez **ordre est prêt à être traité**.  
  
    2.  Cliquez sur le **de** propriété, puis tapez  **orders@globalbank.com** .  
  
    3.  Cliquez sur le **MessagePartsAttachment** propriété, puis tapez **2**.  
  
    4.  Cliquez sur le **sujet** propriété, puis tapez **afin que {givenName}**.  
  
    5.  Configurer le **SMTPAuthentication, SMTPHost, nom d’utilisateur,** et **mot de passe** propriétés à l’aide des informations de connexion pour votre environnement local.  
  
    6.  Cliquez sur **OK** pour fermer la **Configuration de point de terminaison** boîte de dialogue.  
  
5.  Cliquez sur le **LdapResolver** programme de résolution, puis cliquez sur **Configuration du programme de résolution de Test**.  
  
6.  Dans la fenêtre Sortie, vérifiez que l’objet dans le résolu **Configuration de point de terminaison** valeur est **afin que John**, puis vérifiez que le résolu **Transport emplacement** est le envoyer par courrier électronique adresse associée au compte de l’utilisateur dans Active Directory (par exemple, johne@globalbank.com).  
  
7.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessageEmail** élément de modèle.  
  
8.  Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteMessageEmail** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **EmailNAOrderDoc**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
9. Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteMessageEmail** élément de modèle et la **EmailNAOrderDoc**élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **EmailNAOrderDoc**, puis cliquez sur **gestionnaires d’envoi**.  
  
10. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **RouteMessageEmail** élément de modèle à la **SendPortFilter** élément de modèle.  
  
11. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **EmailNAOrderDoc** élément de modèle.  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **LdapResolution** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  La version XML de l’itinéraire s’ouvre dans Visual Studio.  
  
2.  Enregistrez tous les artefacts de projet.  
  
3.  Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (LdapResolution.xml).  
  
#### <a name="to-test-the-itinerary"></a>Pour tester la feuille de route  
  
1.  Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).  
  
2.  Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.  
  
3.  Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries. Sélectionnez **LdapResolution.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.  
  
4.  Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.  
  
5.  Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.  
  
6.  Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos. Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.  
  
7.  Cliquez sur le **soumettre la demande** bouton. Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.  
  
8.  Ouvrez Microsoft Outlook Express (ou le client de messagerie de votre choix) et la vérification de la remise du message au message électronique de John Evans.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Utilisation de la résolution et du routage dynamiques](../esb-toolkit/using-dynamic-resolution-and-routing.md)