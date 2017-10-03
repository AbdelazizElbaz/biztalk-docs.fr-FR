---
title: "Étape 1 : Utiliser l’Assistant développement d’adaptateurs pour créer le projet Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ea0e33c-0d8d-4656-a6f0-3008b90f93f8
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a63953b0928915a8fea5b357722cd4e34f1b900c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-use-the-adapter-service-development-wizard-to-create-the-web-project"></a>Étape 1 : Utiliser l’Assistant développement d’adaptateurs pour créer le projet Web
![Étape 1 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **Durée :** 10 minutes  
  
 Dans cette étape, vous créez un projet à l’aide de Visual Studio et le [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]. Le [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] recueille des informations sur la carte, les opérations et les configurations de point de terminaison et génère un projet Web qui peut ensuite être déployé sur IIS.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez générer et déployer l’exemple Echo décrit dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) avant de commencer ce didacticiel.  
  
### <a name="to-start-the-adapter-service-development-wizard"></a>Pour démarrer l’Assistant développement d’adaptateurs  
  
1.  Démarrez Visual Studio et, à la **fichier** menu, pointez sur **nouveau**, puis cliquez sur **Site Web**.  
  
2.  Dans le **nouveau Site Web** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Langage**|Cliquez sur **Visual C#**.|  
    |**Modèles**|Cliquez sur **Service d’adaptateur WCF**.|  
    |**Emplacement**|Sélectionnez **système de fichiers**, puis tapez **C:\Tutorials\EchoWeb** en tant que le chemin d’accès.|  
  
3.  Cliquez sur **OK**.  
  
4.  Sur le **page d’accueil**, cliquez sur **suivant**.  
  
### <a name="to-select-the-adapter-and-uri"></a>Pour sélectionner l’adaptateur et l’URI  
  
1.  Sur le **choisissez les opérations pour générer un contrat de service** page, sélectionnez **echoAdapterBindingV2** à partir de la **sélectionner une liaison** déroulante liste, puis cliquez sur  **Configurer**.  
  
2.  Sur le **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue, définissez **type d’information d’identification Client** à **nom d’utilisateur**, puis définissez le  **Informations d’identification utilisateur** comme suit :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom d'utilisateur**|username|  
    |**Mot de passe**|password|  
  
    > [!NOTE]
    >  Le nom d’utilisateur et un mot de passe entré ici sont uniquement utilisées pour se connecter à l’adaptateur lors de l’exécution de la procédure dans l’Assistant et ne sont pas conservées une fois l’Assistant terminé.  
  
3.  Cliquez sur le **propriétés URI** onglet, puis définissez les propriétés comme suit :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Application**|LobApplication|  
    |**EnableAuthentication**|True|  
    |**Nom d’hôte**|lobhostname|  
    |**EchoInUpperCase**|False|  
  
    > [!NOTE]
    >  Les propriétés de l’URI sélectionnées ici permet de créer le \< **client**>\<**point de terminaison**> dans le fichier web.config.  
  
4.  Cliquez sur le **propriétés de liaison** onglet. Notez les valeurs par défaut, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Les valeurs de liaison permet de générer le \< **liaisons**>\<**echoAdapterBindingV2**> dans le fichier web.config.  
  
### <a name="to-select-the-contract-and-operations"></a>Pour sélectionner le contrat et les opérations  
  
1.  Sur le **choisissez les opérations pour générer un contrat de service** , cliquez sur **connexion**.  
  
2.  Dans le **sélectionner une catégorie** d’arborescence, sélectionnez **catégorie principale**. Cette opération remplit le **catégories et opérations disponibles** liste.  
  
    > [!NOTE]
    >  Vous pouvez également entrer un terme à rechercher dans le **recherche dans la catégorie** champ à rechercher toutes les opérations qui contiennent le terme de recherche.  
  
3.  Dans le **catégories et opérations disponibles** liste, sélectionnez **EchoGreetings** et cliquez sur **ajouter**. Cette opération déplace l’opération EchoGreetings le **ajouté des catégories et opérations** liste. Les opérations sélectionnées ici seront exposées à des applications clientes via le code du proxy client généré par l’Assistant.  
  
     ![Sélectionnez le contrat et les opérations](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/de497b32-c820-480f-84f3-a9d0d2ded86b.gif "de497b32-c820-480f-84f3-a9d0d2ded86b")  
  
4.  Cliquez sur **Suivant**.  
  
### <a name="to-configure-service-and-endpoint-behavior"></a>Pour configurer le comportement de service et de point de terminaison  
  
1.  Sur le **configurer les comportements de service et de point de terminaison** , entrez les valeurs suivantes pour **Configuration de comportement de Service**:  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**EnableMetadataExchange**|True|  
    |**IncludeExceptionDetailsinFault**|True|  
    |**Nom**|customServiceBehavior|  
    |**UseServiceCertificate**|False|  
  
     Ces valeurs sont utilisées pour remplir la \< **serviceBehaviors**>.  
  
2.  Entrez les valeurs suivantes pour **Configuration de comportement de point de terminaison**:  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**Nom**|customEndpointBehavior|  
    |**AuthenticationType**|**HTTPUsernamePassword**|  
    |**UsernameHeader**|MyUserHeader|  
    |**PasswordHeader**|MyPassHeader|  
  
     Ces valeurs permet de spécifier le **adapterSecurityBridgeType** dans le <**endpointBehaviors** élément web.confg.  
  
     ![Configuration de point de terminaison](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3fd5784c-64e5-47c1-9a6f-10f12f77f726.gif "3fd5784c-64e5-47c1-9a6f-10f12f77f726")  
  
3.  Cliquez sur **Suivant**.  
  
### <a name="to-configure-the-binding"></a>Pour configurer la liaison  
  
1.  Sur le **configurer la liaison de point de terminaison de service et l’adresse** page, sélectionnez le **BindingConfiguration** entrée dans **configurer la liaison pour le contrat et l’adresse**, et puis cliquez sur le bouton de sélection (**...** ) bouton.  
  
2.  Dans le **personnaliser la liaison de** boîte de dialogue, définissez **Mode** à **TransportWithMessageCredential**, puis cliquez sur **OK**.  
  
3.  Cliquez sur **appliquer**, puis cliquez sur **suivant**.  
  
4.  Sur le **Résumé** page, passez en revue les contrats et les opérations sélectionnées pour ce projet, puis cliquez sur **Terminer**. Vous verrez la solution EchoWeb, qui contient les fichiers projet créés par le[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez utilisé le [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] pour générer un site Web qui, projeter le moment où il est publié sur le serveur IIS, hébergera développé par l’adaptateur de l’écho dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) dans IIS. Le projet Web résultant permet des clients WCF et les Services Web accéder aux opérations sélectionnées.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour générer et déployer le projet Web, passez à [étape 2 : déployer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)