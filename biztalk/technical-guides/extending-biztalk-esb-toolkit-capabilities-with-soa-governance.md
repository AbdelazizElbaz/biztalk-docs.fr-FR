---
title: "Extension des capacités de boîte à outils BizTalk ESB avec la gouvernance SOA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b66a121b-d86f-4f97-a05f-5141ffe719e8
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f872d24c7c792d01f80463da0e3c27f31d76d8ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-biztalk-esb-toolkit-capabilities-with-soa-governance"></a>Extension des capacités de boîte à outils BizTalk ESB avec la gouvernance SOA
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est livré avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et est une collection d’outils et les bibliothèques qui étendent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fonctionnalités de prise en charge une architecture de messagerie faiblement couplée et dynamique. Il fonctionne comme un intergiciel (middleware) qui fournit des outils pour assurer la médiation rapide entre les services et leurs clients. L’activation d’une flexibilité maximale en cours d’exécution, le [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] simplifie la composition faiblement couplée de points de terminaison de service et de gestion des interactions de service.  
  
 Sentinet BizTalk Server Extensions pour améliorer les fonctionnalités du [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] en l’intégrant Sentinet, une gouvernance de SOA et de la solution de logiciel de gestion des API pour la plate-forme Microsoft. La première version de la Sentinet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] propose des Extensions un [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] résolveur de référentiel SOA qui s’intègre à BizTalk Server 2013, [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]et Visual Studio 2012.  
  
 Étend le programme de résolution Sentinet SOA entretiens de ce livre blanc sur la façon dont [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] capacités, comment configurer le programme de résolution Sentinet SOA et enfin un exemple montrant comment utiliser le programme de résolution Sentinet SOA.  
  
## <a name="esb-toolkit-and-sentinet-soa-resolver"></a>ESB Toolkit et le programme de résolution Sentinet SOA  
 Entre autres choses, un programme de résolution ESB Toolkit doit fournir les éléments suivants :  
  
-   Résolution de runtime de points de terminaison de service et leurs configurations  
  
-   Solutions BizTalk ESB avec messagerie faiblement couplée.  
  
 Sentinet offre un robuste et complète [SOA référentiel](http://www.nevatech.com/sentinet/soa-repository) qui fournit des fonctionnalités de gestion des solutions d’intégration SOA, ainsi que de la gouvernance SOA avancé et d’exécution. Fournit de programme de résolution Sentinet SOA combiné avec Sentinet SOA référentiel, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architectures ESB avec les configurations de ESB avancées et facile à utiliser, de routage dynamique des messages et de fonctionnalités de mise en œuvre de sécurité de message.  
  
 Un diagramme ci-dessous montre comment le programme de résolution SOA Sentinet s’ajuste à la [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] architecture.  
  
 ![Sentinet avec BizTalk ESB Toolkit](../technical-guides/media/sentinetwp-arch.png "SentinetWP_Arch")  
  
 Lors de l’exécution, le **résolution de point de terminaison et de routage** composant dans l’illustration ci-dessus (qui fait partie de l’infrastructure de programme de résolution ESB Toolkit) utilise un document de feuille de route (créé dans le Concepteur de feuille de route de Visual Studio) pour instancier programme de résolution spécifique et vous demande le programme de résolution pour fournir le point de terminaison de service et sa configuration. Itinéraire lui-même doit être configuré avec la référence au point de terminaison de service, afin que le programme de résolution peut utiliser cette référence pour rechercher le point de terminaison demandé dans le Registre ou le référentiel. Au moment du design (lors de la création de la feuille de route), une adresse physique réelle du point de terminaison de service n’est pas connue, et ne le sont pas les stratégies de sécurité nécessaires au service. À des étapes ultérieures, ESB Toolkit runtime utilise résolu le point de terminaison de service pour configurer le Port d’envoi dynamique rampe pour envoyer le message à l’adresse de service physique réel avec les paramètres de sécurité de service requis. Si l’adresse de point de terminaison de service, des protocoles de communication ou des spécifications de sécurité modifient uniquement la configuration du Registre/référentiel doit être mis à jour. La configuration de l’exécution des artefacts ESB ou BizTalk Server ne nécessite pas d’être mis à jour.  
  
## <a name="how-does-the-sentinet-resolver-add-value-to-an-esb-toolkit-application"></a>Comment le programme de résolution Sentinet Ajouter valeur à une application d’ESB Toolkit ?  
 Les deux principaux avantages de l’utilisation de l’outil de résolution de Sentinet, ainsi que le référentiel SOA sont :  
  
-   Affectation d’identification du client pour le point de terminaison de service externe résolu : la plupart du temps, le point de terminaison ESB résolu nécessite l’identité du client spécifique pour appeler un service externe (par exemple, le nom d’utilisateur/mot de passe, les informations d’identification du compte Windows spécifiques ou X.509 spécifique certificat). Il s’agit d’une condition de sécurité très courant qui n’est pas correctement gérée par les autres programmes de résolution/registres de ESB.  
  
-   Restreindre l’accès aux informations de sécurité : pour contourner la limitation précédente, autres programmes de résolution peuvent utiliser une configuration manuelle d’éléments tModels complexe fichier XML avec les identités de sécurité requis. Toutefois, l’enregistrement des informations de sécurité dans le cadre des registres/dépôts n’est pas l’approche appropriée. Cela fournit le service aux consommateurs un accès facile aux détails de sécurité telles que le nom d’utilisateur, mot de passe, etc. pour accéder au service.  
  
 Programme de résolution de Sentinet et Sentinet SOA référentiel offrent des fonctionnalités à avec souplesse et en toute sécurité d’affecter l’identité de n’importe quel client spécifique au point de terminaison ESB résolu via les comportements de point de terminaison WCF standard ou personnalisées. Sentinet à cette fin, en configurant le programme de résolution de Sentinet et pas le référentiel de SOA Sentinet avec les informations de sécurité. Toutes les informations d’identification de client sont configurées avec le programme de résolution de Sentinet sont stockées sous forme chiffrée.  
  
 Au-delà de cela, voici quelques-unes des autres avantages de l’utilisation du programme de résolution de Sentinet et le Sentinet SOA référentiel.  
  
-   Fournit un référentiel SOA complet. L’espace de stockage fournit l’accès au contenu des métadonnées de service, les identités de service et les stratégies, prise en charge des versions de service, etc..  
  
-   Facilité d’inscription des services physiques dans le Registre Sentinet en téléchargeant le service WSDL.  
  
-   Complète et facile à utiliser Sentinet Console d’administration. La console fournit l’accès à toutes les métadonnées de service et des artefacts associé à interface utilisateur simple pour les opérations de service d’accès et leurs schémas de données, les points de terminaison de service, les stratégies de sécurité, etc..  
  
-   Gestion et la configuration de comportements personnalisés pour les points de terminaison résolus. Programme de résolution de Sentinet fournit les comportements de point de terminaison entièrement personnalisable et facile à configurer des points de terminaison résolus.  
  
-   Option permettant de configurer le programme de résolution de Sentinet avec une variété de critères de recherche. Itinéraires peuvent définir n’importe quel mot clé qui est affectée à un point de terminaison de service, ou utilisez un chemin d’accès de service qui pointe vers un service dans la hiérarchie des services de référentiel.  
  
-   Programme de résolution avancée capacités de test. Configurations de Sentinet résolution peuvent être testées directement à partir du Concepteur d’itinéraire de Visual Studio. Alors que les autres programmes de résolution ne permet plus d’informations sur les propriétés de base du point de terminaison, programme de résolution de Sentinet fournit des informations étendues sur les points de terminaison résolus. En plus des propriétés de base de point de terminaison, programme de résolution Sentinet révèle les propriétés qui identifient résolu l’emplacement de service et de point de terminaison dans le référentiel de Sentinet. Concepteurs d’itinéraire peuvent tester comment Sentinet le programme de résolution et de ses différents critères de recherche affectent les résultats de résolution avant de l’itinéraire lui-même est utilisé lors de l’exécution.  
  
## <a name="installing-the-sentinet-biztalk-server-extensions"></a>L’installation des Extensions Sentinet BizTalk Server  
 Vous pouvez télécharger et installer les Extensions de BizTalk Sentinet de [ici](http://www.nevatech.com/download). Installation de l’extension installe le programme de résolution de Sentinet pour ESB Toolkit, documentation et des exemples sur la façon d’utiliser l’extension.  
  
 Un document détaillant comment installer et configurer l’extension Sentinet BizTalk Server est disponible dans le cadre du téléchargement du produit.  
  
## <a name="using-the-sentinet-biztalk-server-extensions"></a>Utilisation des Extensions serveur Sentinet BizTalk  
 Dans cette section, nous examiner comment utiliser les extensions de Sentinet BizTalk Server et montre les capacités mentionnées ci-dessus.  
  
### <a name="prerequisites"></a>Conditions préalables  
 Instructions contenues dans ce livre blanc supposent que vous avez installé et configuré suivantes :  
  
-   Visual Studio 2012.  
  
-   BizTalk Server 2013. Pour obtenir des instructions, consultez [l’installation de BizTalk Server 2013](http://msdn.microsoft.com/library/jj248688\(v=bts.80\).aspx).  
  
-   Serveur BizTalk ESB Toolkit. Pour obtenir des instructions, consultez [installer et configurer Microsoft BizTalk ESB Toolkit](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx).  
  
-   Extensions serveur Sentinet BizTalk. Pour obtenir des instructions, consultez la documentation disponible dans le cadre du téléchargement du produit disponible [ici](http://www.nevatech.com/download).  
  
### <a name="register-a-web-service"></a>Inscrire un service web  
 Les services Web qui sont gérés par l’infrastructure de Sentinet doivent être inscrit dans le référentiel. Ce livre blanc utilise un exemple de service WCF client recherche qui est livré avec le package d’installation Sentinet.  
  
1.  Démarrer le **client recherche** exemple de service installé par le package d’installation Sentinet. Lancez l’exemple de recherche du client en tant qu’administrateur, sélectionnez une stratégie de liaison (par exemple, **wsHttpBinding**), puis **Démarrer**.  
  
2.  Une fois que le service est en cours d’exécution, cliquez sur le **vue Wsdl** lien pour ouvrir un navigateur avec l’URL des métadonnées de service et le service WSDL. Copiez l’URL des métadonnées à partir de la barre d’adresses du navigateur.  
  
3.  Ouvrez un navigateur et entrez l’URL (`https://[computer-name]/sentinet`) pour démarrer la Console d’administration Sentinet. Nom de connexion et sélectionnez le **référentiel** élément racine dans le **référentiel** panneau d’affichage. Avec le bouton droit le **référentiel** élément racine et cliquez sur le **Ajouter > Service > SOAP** option de menu.  
  
4.  Dans le **ajouter un Service** boîte de dialogue, pour le **WSDL à partir de l’URL** option, collez l’URL de métadonnées de service vous avez copiée précédemment, puis cliquez sur **suivant**.  
  
     ![Ajouter l’URL du Service](../technical-guides/media/sentinetwp-addserviceurl.png "SentinetWP_AddServiceURL")  
  
5.  L’Assistant commence à télécharger les métadonnées du service. Une fois le téléchargement terminé, l’Assistant affiche l’arborescence du Service Web. Fournissez un nom pour le service et cliquez sur **Terminer** pour télécharger les métadonnées du service dans le référentiel de Sentinet.  
  
     ![Structure de service de site Web](../technical-guides/media/sentinetwp-servicestructure.png "SentinetWP_ServiceStructure")  
  
6.  Le service est importé dans le référentiel en tant que version 1. Sélectionnez la version, puis le point de terminaison. Dans le **détails du point de terminaison** volet en bas, cliquez sur le **des pièces jointes** onglet, puis cliquez sur **modifier**.  
  
     ![Modifier le point de terminaison de service](../technical-guides/media/sentinetwp-serviceendpoint.png "SentinetWP_ServiceEndpoint")  
  
7.  Dans l’onglet Détails du point de terminaison, cliquez sur le (**+**) signer contre **mots clés**, entrez un mot clé à associer le point de terminaison (par exemple, **TestKeyword**), et puis cliquez sur **enregistrer**. Le mot clé est utilisé comme une étiquette de point de terminaison (ou identificateur) dans le référentiel SOA.  
  
     ![Spécifiez un mot clé](../technical-guides/media/sentinetwp-enterkeyword.png "SentinetWP_EnterKeyword")  
  
 Répétez les étapes ci-dessus pour ajouter une nouvelle version de la **CustomerSearch** service, mais avec une liaison différente, par exemple, **basicHttpBinding**. Plus loin dans ce livre blanc, nous vous montrer comment le programme de résolution de Sentinet peut résoudre pour différents services (ou des versions différentes du même service) simplement en associant un mot clé de recherche pour le point de terminaison de service.  
  
### <a name="configure-sentinet-resolver"></a>Configurer le programme de résolution de Sentinet  
 Cette section montre comment configurer le programme de résolution de Sentinet dans un projet BizTalk ESB itinéraire concepteur simple et plus précisément l’utilisation des mots clés pour résoudre identifie de façon unique un point de terminaison de service. Cette section montre également comment tester le programme de résolution à partir de Visual Studio, sans envoyer les messages d’ESB.  
  
1.  Démarrez Visual Studio et créez un **le Concepteur d’itinéraire ESB BizTalk** projet.  
  
2.  Dans l’Explorateur de solutions, double-cliquez sur la feuille de route pour l’ouvrir dans le Concepteur d’itinéraire.  
  
3.  À partir de la boîte à outils, faites glisser et déposez le **itinéraire Service** forme sur l’aire du concepteur.  
  
4.  Sélectionnez le **itinéraire Service** mettre en forme et de modifier le **d’extension du Service itinéraire** propriété **extendeur de messagerie** dans la liste déroulante.  
  
     ![Définir la propriété d’extendeur Message](../technical-guides/media/sentinetwp-setmessageextender.png "SentinetWP_SetMessageExtender")  
  
5.  Avec le bouton droit le **résolveur** élément dans le **itinéraire Service** mettre en forme et cliquez sur **ajouter le nouveau programme de résolution**.  
  
     ![Ajouter un nouveau programme de résolution](../technical-guides/media/sentinetwp-addnewresolver.png "SentinetWP_AddNewResolver")  
  
6.  Sélectionnez le nouvel élément de programme de résolution, renommez-le (par exemple, **MyResolver**) et pour le **implémentation d’un programme de résolution** propriété, sélectionnez **Sentinet programme de résolution d’Extension**.  
  
     ![Définir l’implémentation du résolveur](../technical-guides/media/sentinetwp-addresolverimplementation.png "SentinetWP_AddResolverImplementation")  
  
7.  Spécifiez le **Action** et **mots clés** propriétés pour l’Extension du programme de résolution Sentinet. Nous allons utiliser ces propriétés pour résoudre identifie de façon unique aux services que nous avons ajoutés précédemment dans le référentiel de Sentinet. Il existe des autres propriétés que vous pouvez spécifier pour l’Extension du programme de résolution Sentinet. Pour en savoir plus sur ces propriétés, reportez-vous au Guide de l’utilisateur de Sentinet BizTalk Extensions.  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |Action|En-tête d’Action de message qui identifie de façon unique une opération de service qui est appelée. Cet en-tête action fait partie du service WSDL et se trouve dans le WSDL du service, ou à partir de l’Interface utilisateur Sentinet la Console d’administration (sous les propriétés du message de demande de l’opération.|  
    |Mots clés|Fournissez le mot clé (par exemple, **TestKeyword**) que vous avez affecté au service dans la Console d’administration Sentinet.|  
  
     La capture d’écran suivante montre la propriété d’Action et les mots clés spécifiée pour le **MyResolver** configuration.  
  
     ![Configuration de Sentinet Resolvery](../technical-guides/media/sentinetwp-resolverconfig.png "SentinetWP_ResolverConfig")  
  
8.  Enregistrez les modifications apportées à la configuration.  
  
#### <a name="advanced-resolver-configuration"></a>Configuration du programme de résolution avancées  
 Configuration des Extensions Sentinet BizTalk application modifie **Sentinet.BizTalk.config** fichier situé à la racine du dossier d’installation du package (l’emplacement par défaut est `<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Sentinet.BizTalk.config`). Le fichier peut être modifié en dehors de **Configuration des Extensions Sentinet BizTalk** application pour fournir des options de configuration avancées. Par exemple, dans de nombreux scénarios ESB pratiques résolus des points de terminaison doivent être fournis avec les liaisons et les adresses de point de terminaison de service, mais également avec des identités client spécifique (nom d’utilisateur/mot de passe, informations d’identification du compte Windows spécifiques ou un client X.509 certificat). L’identité du client approprié, Ports d’envoi ESB rampe de ne pas sans appeler des services externes. Programme de résolution de Sentinet permet de développeur de l’itinéraire affecter un comportement de point de terminaison spécifique qui fournit des identités de point de terminaison client approprié. Plusieurs comportements de point de terminaison peuvent être préconfigurés comme des comportements de point de terminaison WCF standard dans le **Sentinet.BizTalk.config** fichier et le comportement de point de terminaison spécifique puis peuvent être référencée dans l’itinéraire à partir de l’outil de résolution de Sentinet configuration, en spécifiant le nom du comportement pour la **résolu de comportement de point de terminaison** propriété.  
  
### <a name="test-the-resolver-configuration"></a>Tester la Configuration du programme de résolution  
 Après avoir configuré le programme de résolution de Sentinet en spécifiant les valeurs de propriété approprié, vous pouvez tester le programme de résolution à partir de Visual Studio.  
  
1.  À partir de l’aire de conception, cliquez sur le programme de résolution Sentinet que vous avez ajouté à la **itinéraire Service** mettre en forme, puis cliquez sur **Configuration du programme de résolution de Test**.  
  
     Le volet de sortie affiche les résultats des tests, un extrait de ce qui est similaire à indiqué ci-dessous :  
  
    ```  
    ***** Resolved Service Endpoint *****  
  
    Service Path and Name          : /CustomerSearch  
    Service Id                     : 2b6d686a-cae1-4b7b-93da-99affef98478  
    Service Version                : 1  
    Endpoint Name                  : WSHttpBinding_ICustomerSearch  
    Endpoint Address               : http://btscloudcar/CustomerSearch/1  
    ```  
  
     Notez que le programme de résolution retournée le point de terminaison pour le **CustomerSearch** service **Version 1** à laquelle les critères de recherche (**TestKeyword**) est attaché.  
  
2.  Supprimer le **TestKeyword** associé à la **Version 1** de la **CustomerSearch** de service et l’associer à un point de terminaison de la deuxième version du service.  
  
    1.  Ouvrez la Console d’administration de Sentinet, cliquez sur **Version 1** sous le **CustomerSearch** de service et cliquez sur le point de terminaison wsHttpBinding, puis cliquez sur le **des pièces jointes** onglet, puis cliquez sur **modifier**.  
  
         ![Supprimez le mot clé à partir du service CustomerSearch](../technical-guides/media/sentinetwp-removekeyword.png "SentinetWP_RemoveKeyword")  
  
    2.  Cliquez sur le bouton sur le mot clé que vous avez entré avant de supprimer le mot clé, cliquez sur **Oui** dans la boîte de message, puis cliquez sur **enregistrer**.  
  
         ![Supprimez le mot clé à partir du service CustomerSearch](../technical-guides/media/sentinetwp-removekeyword-2.png "SentinetWP_RemoveKeyword_2")  
  
    3.  À présent, attribuer le même mot clé (**TestKeyword**) pour le **basicHttpBinding** point de terminaison sous la **Version 2** du même service.  
  
3.  Revenez à Visual Studio et à nouveau la configuration du programme de résolution de test. Cliquez sur le programme de résolution Sentinet que vous avez ajouté à la **itinéraire Service** mettre en forme, puis cliquez sur **Configuration du programme de résolution de Test**.  
  
     Le volet de sortie affiche les résultats des tests, un extrait de ce qui est similaire à indiqué ci-dessous :  
  
    ```  
    ***** Resolved Service Endpoint *****  
  
    Service Path and Name          : /CustomerSearch  
    Service Id                     : 5b9e5878-7016-44ab-9f0e-5282a8c3e508  
    Service Version                : 2  
    Endpoint Name                  : BasicHttpBinding_ICustomerSearch  
    Endpoint Address               : http://btscloudcar/CustomerSearch/2  
    ```  
  
4.  Notez comment le programme de résolution retournée maintenant les détails de la **Version 2** du service même si vous n’avez pas modifié n’importe où dans l’application de la feuille de route ESB.  
  
 Affecter le mot clé (**TestKeyword**) à la version 1 du service (avec la **WSHttpBinding** point de terminaison).  
  
## <a name="using-the-sentinet-biztalk-server-extensions"></a>Utilisation des Extensions serveur Sentinet BizTalk  
 Dans cette section, nous allons étudier comment l’Extension de BizTalk Sentinet, ainsi que le programme de résolution ESB, peut servir à identifier de façon unique un service et acheminer le message à ce service, avec peu ou aucune modification pour le service ou le client qui envoie le message. Nous testerons deux scénarios :  
  
-   Envoyer un exemple de message à un service inscrit dans le référentiel de Sentinet (avec le mot clé attaché). Ensuite, modifiez la stratégie de liaison pour le service à l’aide de la Console d’administration Sentinet et envoyer un autre exemple de message. Ce scénario montre comment modifier la stratégie de sécurité du service ni affecte l’application cliente, ni l’itinéraire ESB.  
  
-   Envoyer un exemple de message à un point de terminaison inscrit dans le référentiel de Sentinet (avec le mot clé attaché). Ensuite, attachez le même mot clé à une autre version du même service et renvoyez le message. Ce scénario montre comment attacher un mot clé pour une version différente du service automatiquement route les messages vers une nouvelle version de service.  
  
 Pour tester ces scénarios, nous allons utiliser les exemples suivants :  
  
-   **Service de recherche de client** fourni avec le programme d’installation de Sentinet. Ce service peut être démarré à partir du menu Démarrer.  
  
-   **Nevatech.Vsb.BizTalk.Samples** solution fournie avec le programme d’installation de Sentinet. Cet exemple est disponible à l’adresse `<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples`.  
  
-   ESB. Exemple de Itinerary.Test livré avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. Cette option est disponible à `<install drive>:\Program Files (x86)\Microsoft BizTalk ESB Toolkit\ESBSource.zip\Source\Samples\Itinerary\Source\ESB.Itinerary.Test` et est utilisé pour tester les exemples de messages pour le Service de recherche du client.  
  
#### <a name="to-test-the-sentinet-resolver-by-changing-the-service-policy-binding"></a>Pour tester le programme de résolution de Sentinet en modifiant les liaisons de stratégie de service  
  
1.  Assurez-vous que le **CustomerSearch** service que vous avez déployé avec la liaison wsHttpBinding est en cours d’exécution.  
  
2.  À partir de la **Nevatech.Vsb.BizTalk.Samples** exemple, ouvrez **CustomerSearch.Search.itinerary**, sélectionnez **résoudre le point de terminaison Service** sous le **Message Extendeur** au sein de la **router un Message** forme et pour le **mots clés** propriété, spécifiez un mot clé, tel que **TestKeyword**.  
  
     ![Attribuer mot-clé](../technical-guides/media/sentinetwp-assignkeyword.png "SentinetWP_AssignKeyword")  
  
3.  Enregistrez les modifications dans la feuille de route et exporter le modèle. Avec le bouton droit n’importe où sur l’aire du Concepteur d’itinéraire et cliquez sur **exporter le modèle**.  
  
4.  Dans la Console Administration de BizTalk Server, cliquez sur le **Microsoft.Practices.ESB** application, cliquez sur Importer, puis cliquez sur liaisons. Accédez à l’emplacement d’exemple de programme de résolution ESB à `<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver`, puis ouvrez le **BizTalk.Bindings.xml** fichier. Cette opération crée le **Sentinet avec sollicitation-réponse** et **Sentinet unidirectionnel** requis pour les itinéraires de l’exemple de ports d’envoi.  
  
     En outre, assurez-vous que tous les ports d’envoi et réception des emplacements de la **Microsoft.Practices.ESB** application BizTalk sont enregistrées et démarré.  
  
5.  Ouvrez le **ESB. Itinerary.Test** application, générez-le et l’exécuter. Dans le Client de Test d’itinéraire qui est lancé, procédez comme suit :  
  
    1.  Dans le Client de Test d’itinéraire, sous **Options du Service Web**, désactivez **utiliser le Service WCF**, puis sélectionnez **deux manière Service**.  
  
    2.  À partir de la **Service Type** liste déroulante, sélectionnez **messagerie**.  
  
    3.  Cliquez sur **charge itinéraire** et accédez à la **CustomerSearch.Search.Itinerary.xml** fichier situé dans l’exemple de projet **ExportedItineraries** dossier `<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\ExportedItineraries`.  
  
    4.  Cliquez sur le bouton de sélection (**...** ) sous **charge Message** de groupe et accédez à **CustomerSearch.Search.Request.xml** situé dans le fichier **SampleMessages** dossier `<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\SampleMessages`.  
  
    5.  Cliquez sur **soumettre la demande de** et vérifiez que la réponse dans reçu.  
  
6.  Sur le **CustomerSearch** boîte de dialogue, notez que le compteur est incrémenté.  
  
7.  Dans la Console d’administration Sentinet, mettre à jour les détails du point de terminaison à utiliser le basicHttpBinding au lieu de wsHttpBinding.  
  
    1.  Sélectionnez le point de terminaison de service, cliquez sur le **détails** onglet, puis cliquez sur **modifier**.  
  
    2.  Dans le **détails** , cliquez sur le bouton de sélection (**...** ) dans le **stratégie** section, pour lancer le **modifier la stratégie** Assistant.  
  
         ![Lancer l’Assistant de modifier la stratégie](../technical-guides/media/sentinetwp-modifypolicy-1.png "SentinetWP_ModifyPolicy_1")  
  
    3.  Sur la première page, conserver le type de stratégie en tant que **privé** puis cliquez sur **suivant**.  
  
    4.  Dans la deuxième page, modifiez le **wsHttpBinding** élément XML à **basicHttpBinding** (respecte la casse), puis cliquez sur **Terminer**.  
  
         ![Mise à jour de la liaison des stratégies](../technical-guides/media/sentinetwp-modifypolicy-2.png "SentinetWP_ModifyPolicy_2")  
  
    5.  Cliquez sur **enregistrer** pour enregistrer les modifications dans les détails du point de terminaison.  
  
8.  Arrêter le **CustomerSearch** de service, modifiez la liaison à partir de **wsHttpBinding** à **basicHttpBinding**, puis redémarrez le service.  
  
     ![Redémarrer le service avec une liaison différente](../technical-guides/media/sentinetwp-restartcustservice.png "SentinetWP_RestartCustService")  
  
9. À partir de la **tester le Client itinéraire**, renvoyer un message de test pour le service de recherche du client. Notez que le compteur dans la boîte de dialogue de Service de recherche de client est à nouveau incrémenté de 1.  
  
     Une fois que le message est reçu avec succès, à partir de la Console d’Administration Sentinet, modifiez la stratégie de détails au **wsHttpBinding**. De même, arrêtez le **client recherche** de service, modifiez la stratégie à wsHttpBinding et démarrer le service.  
  
 Cela montre comment les détails du service dans le référentiel de Sentinet peuvent être mis à jour à la volée à cibler un point de terminaison de service mis à jour sans modifier la feuille de route ou le client.  
  
#### <a name="to-test-the-sentinet-resolver-by-changing-keyword-assignments"></a>Pour tester le programme de résolution de Sentinet en modifiant les affectations de mot clé  
  
1.  Assurez-vous que les deux instances de **CustomerSearch** service que vous avez déployé avec la wsHttpBinding et basicHttpBinding sont en cours d’exécution.  
  
2.  À partir de la **Nevatech.Vsb.BizTalk.Samples** exemple, ouvrez **CustomerSearch.Search.itinerary**, sélectionnez **résoudre le point de terminaison Service** sous le **Message Extendeur** au sein de la **router un Message** forme et pour le **mots clés** propriété, spécifiez un mot clé, tel que **TestKeyword**.  
  
     ![Attribuer mot-clé](../technical-guides/media/sentinetwp-assignkeyword.png "SentinetWP_AssignKeyword")  
  
3.  Enregistrez les modifications dans la feuille de route et exporter le modèle. Avec le bouton droit n’importe où sur l’aire du Concepteur d’itinéraire et cliquez sur **exporter le modèle**.  
  
4.  Dans la Console Administration de BizTalk Server, cliquez sur le **Microsoft.Practices.ESB** application, cliquez sur Importer, puis cliquez sur liaisons. Accédez à l’emplacement d’exemple de programme de résolution ESB à `<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver`, puis ouvrez le **BizTalk.Bindings.xml** fichier. Cette opération crée le **Sentinet avec sollicitation-réponse** et **Sentinet unidirectionnel** requis pour les itinéraires de l’exemple de ports d’envoi.  
  
     En outre, assurez-vous que tous les ports d’envoi et réception des emplacements de la **Microsoft.Practices.ESB** application BizTalk sont enregistrées et démarré.  
  
5.  Ouvrez le **ESB. Itinerary.Test** application, générez-le et l’exécuter. Dans le Client de Test d’itinéraire qui est lancé, procédez comme suit :  
  
    1.  Dans le Client de Test d’itinéraire, sous **Options du Service Web**, désactivez **utiliser le Service WCF**, puis sélectionnez **deux manière Service**.  
  
    2.  À partir de la **Service Type** liste déroulante, sélectionnez **messagerie**.  
  
    3.  Cliquez sur **charge itinéraire** et accédez à la **CustomerSearch.Search.Itinerary.xml** fichier situé dans l’exemple de projet **ExportedItineraries** dossier `<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\ExportedItineraries`.  
  
    4.  Cliquez sur le bouton de sélection (**...** ) sous **charge Message** de groupe et accédez à **CustomerSearch.Search.Request.xml** situé dans le fichier **SampleMessages** dossier `<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\SampleMessages`.  
  
    5.  Cliquez sur **soumettre la demande de** et vérifiez que la réponse dans reçu.  
  
6.  Sur le **CustomerSearch** boîte de dialogue, notez que le compteur est incrémenté.  
  
7.  À partir de la Console d’Administration Sentinet, supprimez le **TestKeyword** associé à la **Version 1** de la **CustomerSearch** de service et associez-le à **Version 2** du service.  
  
    1.  Ouvrez la Console d’administration de Sentinet, cliquez sur **Version 1** sous le **CustomerSearch** de service et cliquez sur le point de terminaison wsHttpBinding, puis cliquez sur le **des pièces jointes** onglet, puis cliquez sur **modifier**.  
  
         ![Supprimez le mot clé à partir du service CustomerSearch](../technical-guides/media/sentinetwp-removekeyword.png "SentinetWP_RemoveKeyword")  
  
    2.  Cliquez sur le bouton sur le mot clé que vous avez entré avant de supprimer le mot clé, cliquez sur **Oui** dans la boîte de message, puis cliquez sur **enregistrer**.  
  
         ![Supprimez le mot clé à partir du service CustomerSearch](../technical-guides/media/sentinetwp-removekeyword-2.png "SentinetWP_RemoveKeyword_2")  
  
    3.  À présent, attribuer le même mot clé (**TestKeyword**) pour le **basicHttpBinding** point de terminaison sous la **Version 2** du même service.  
  
8.  Envoyer un message de test à partir de la **Client d’itinéraire Test** et notez que cette fois-ci, le compteur est incrémenté dans la boîte de dialogue qui représente la version 2 du service, déployée avec le basicHttpBinding.