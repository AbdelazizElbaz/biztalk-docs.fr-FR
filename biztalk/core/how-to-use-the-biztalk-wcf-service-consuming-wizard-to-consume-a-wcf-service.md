---
title: "Comment utiliser l’Assistant consommation de Service WCF BizTalk pour utiliser un Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF services, WCF Service Consuming Wizard
- WCF Service Consuming Wizard
- tools, WCF Service Consuming Wizard
- consuming, WCF Service Consuming Wizard
ms.assetid: d5fad2ac-4d98-4720-8026-88ebab78b120
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b218fa44b93211fdb51080d68b429744b5aabf72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service"></a>Utilisation de l'Assistant Consommation de service WCF BizTalk pour utiliser un service WCF
L'infrastructure d'adaptateurs BizTalk offre un moyen d'ajouter des schémas d'adaptateur et des types BizTalk aux projets BizTalk. L'Assistant Consommation de service WCF BizTalk vous permet d'ajouter des adaptateurs d'envoi WCF à un projet BizTalk. Pour les adaptateurs d'envoi WCF, vous devez sélectionner un point de terminaison MEX (Metadata Exchange) existant pour les ports d'envoi. Vous devez ensuite entrer les informations utilisées pour générer les schémas et les types. Une fois que l'Assistant est fermé, les schémas et types nécessaires à l'utilisation de services WCF sont ajoutés au projet BizTalk.  
  
### <a name="to-add-the-schemas-and-types-for-wcf-send-adapters-to-your-project"></a>Pour ajouter des schémas et des types pour les adaptateurs d'envoi WCF à votre projet  
  
1.  Dans votre Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans l’Explorateur de solutions, cliquez sur votre projet, cliquez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés - \<**  *nom du projet*  **>**  boîte de dialogue le **modèles** section, Sélectionnez **utiliser le Service WCF**, puis cliquez sur **ajouter**.  
  
3.  Sur le **Bienvenue dans l’Assistant de consommation de Service WCF BizTalk** , cliquez sur **suivant**.  
  
4.  Sur le **source des métadonnées** page, sélectionnez la source des métadonnées à importer, puis cliquez sur **suivant**.  
  
     ![Page source des métadonnées](../core/media/2478a788-23ff-4ba9-a183-82e533b57f46.gif "2478a788-23ff-4ba9-a183-82e533b57f46")  
  
     Pour télécharger des documents de métadonnées du point de terminaison exchange métadonnées d’un service en cours d’exécution, sélectionnez le **point de terminaison MEX (Metadata Exchange)** option. Cela nous permet de créer un port d'envoi qui agit comme un client du service WCF. Pour utiliser cette option, le point de terminaison du service doit publier des métadonnées de service pour extraction à l'aide d'une requête HTTP/GET ou HTTPS/GET. Le point de terminaison du service doit également donner accès aux métadonnées avec des informations d'identification anonymes ou des informations d'identification sous la forme d'un nom d'utilisateur et d'un mot de passe avec le schéma d'authentification de base.  
  
    > [!NOTE]
    >  Avec le schéma d'authentification de base, les informations d'identification sont envoyées en texte clair et peuvent être interceptées facilement. Le schéma n'offre aucune protection pour les informations transmises à partir du service. Vous devez utiliser SSL (Secure Sockets Layer) pour chiffrer vos données.  
  
     Pour les autres documents de métadonnées à importer, sélectionnez le **des fichiers de métadonnées (WSDL et XSD)** option pour importer des métadonnées à partir d’un système de fichiers.  
  
    > [!NOTE]
    >  Certains services ne doivent pas publier de métadonnées. Si vous désactivez la publication des métadonnées, vous réduisez la surface d'attaque de votre service et limitez les risques de divulgation d'informations involontaire.  
  
5.  Si vous avez sélectionné le **point de terminaison MEX (Metadata Exchange)** option sur le **source des métadonnées** page, le **point de terminaison de métadonnées** page s’affiche. Sur le **point de terminaison de métadonnées** page, spécifiez l’URL du service en cours d’exécution qui fournit des métadonnées à télécharger via WS-Metadata Exchange ou Http-Get. Pour obtenir le document de métadonnées à partir de l’URL, cliquez sur **obtenir**. Si le service en cours d’exécution requiert une information d’identification de l’utilisateur avec le schéma d’authentification de base, cliquez sur **modifier** pour ouvrir **l’Assistant de consommation de Service WCF BizTalk** boîte de dialogue dans laquelle vous pouvez fournir le nom d’utilisateur et mot de passe à utiliser lors de l’accès à l’exécution du service.  
  
     ![Page point de terminaison de métadonnées](../core/media/2b17f85a-64d0-4719-99c4-ce61c706f10c.gif "2b17f85a-64d0-4719-99c4-ce61c706f10c")  
  
    > [!NOTE]
    >  Pour télécharger les métadonnées pour les services WCF publiés via HTTP ou HTTPS, vous ne pouvez pas utiliser le point de terminaison MEX tel que http://localhost : 8087/CalculatorService/mex pour le **adresse des métadonnées** zone de texte. Pour les services WCF, vous devez utiliser les métadonnées WSDL pour télécharger les métadonnées comme suit : http://localhost : 8087/CalculatorService ou http://localhost : 8087/CalculatorService ? wsdl  
  
6.  Si vous avez sélectionné le **des fichiers de métadonnées (WSDL et XSD)** option sur le **source des métadonnées** page, le **point de terminaison de métadonnées** page s’affiche. Sur le **point de terminaison de métadonnées** , spécifiez les fichiers de métadonnées à importer. Cliquez sur **ajouter** pour ajouter les fichiers de métadonnées à importer dans le **des fichiers de métadonnées** vue. Cette opération ouvre le **ajouter des fichiers de métadonnées** boîte de dialogue dans laquelle vous pouvez rechercher des emplacements de disque pour les fichiers de métadonnées.  
  
     Dans le **ajouter des fichiers de métadonnées** boîte de dialogue, sélectionnez un ensemble complet de WSDL et XSD fichiers à utiliser pour les métadonnées. Vous pouvez générer ces fichiers de métadonnées en tapant la commande suivante à l'invite de commandes :  
  
     **SvcUtil.exe /t:metadata http://localhost/service.svc/mex**  
  
     Cliquez sur **supprimer** pour supprimer les fichiers de métadonnées sélectionnés dans le **des fichiers de métadonnées** vue.  
  
     ![Page fichiers de métadonnées](../core/media/445bccd1-88b0-41ad-b91d-e899e7d5902d.gif "445bccd1-88b0-41ad-b91d-e899e7d5902d")  
  
    > [!NOTE]
    >  SvcUtil.exe est inclus dans le Kit de développement logiciel Microsoft Windows de Windows Vista et dans les composants d'exécution .NET Framework.  
  
    > [!NOTE]
    >  Les métadonnées de service peuvent être falsifiées ou usurpées en cas de récupération non sécurisée. Des métadonnées falsifiées peuvent rediriger votre client vers un service malveillant, contenir des paramètres de sécurité compromis ou des structures XML malveillantes. Les documents de métadonnées peuvent être très volumineux et sont enregistrés fréquemment dans le système de fichiers. Vous devez vous assurer que les fichiers de métadonnées n'ont pas été falsifiés.  
  
7.  Sur le **récapitulatif des métadonnées de Service WCF importation** page, vérifiez vos paramètres. Vous pouvez cliquer sur **précédent** d’apporter des modifications. Puis cliquez sur **importation** pour créer les artefacts BizTalk et les types à utiliser pour consommer le service WCF.  
  
8.  Sur le **fin de l’Assistant de consommation de Service WCF BizTalk** , cliquez sur **Terminer**. Si vous souhaitez réexécuter cet Assistant, sélectionnez le **réexécuter cet Assistant** option, puis cliquez sur **Terminer**.  
  
     L'Assistant Consommation de service WCF BizTalk crée, dans votre projet BizTalk, les schémas et types BizTalk nécessaires à l'utilisation des services WCF. Les types BizTalk, tels que des types de ports et de messages à parties multiples, sont créés dans une orchestration. Nous vous recommandons de ne pas modifier l'orchestration créée par l'Assistant. Au lieu de cela, vous pouvez ajouter de nouvelles orchestrations dans le projet BizTalk pour vos besoins. L’Assistant de consommation de Service WCF BizTalk crée également deux fichiers de liaison, **BizTalkServiceInstance.BindingInfo.xml** et **BizTalkServiceInstance_Custom.BindingInfo.xml**. **BizTalkServiceInstance.BindingInfo.xml** est un fichier de liaison BizTalk qui peut être importé par l’outil de ligne de commande de développement ou d’un Assistant pour configurer les ports d’envoi avec les adaptateurs WCF de liaison standard, par exemple, le WCF-NetMsmq et WCF-WSHttp cartes. **BizTalkServiceInstance.BindingInfo.xml** est un fichier de liaison BizTalk qui peut être importé par l’outil de ligne de commande de développement ou d’un Assistant pour configurer les ports d’envoi avec l’adaptateur WCF-Custom.  
  
     Lorsque vous importez le fichier de liaison généré, il remplit la **WCF. Action** propriété dans le format de mappage d’action. Pour voir comment cette propriété est configurée, examinez le **Action** zone de texte sur le **général** onglet dans la boîte de dialogue WCF send port transport propriétés dans la console Administration de BizTalk.  
  
     Vous pouvez spécifier le **WCF. Action** propriété de deux manières différentes : le format d’action unique et le format de mappage d’action. Si vous définissez cette propriété dans le format d’action unique, par exemple, http://contoso.com/Svc/Op1 - le **SOAPAction** en-tête pour les messages sortants sont toujours défini sur la valeur spécifiée dans cette propriété. Si vous définissez cette propriété dans le format de mappage d’action, sortant **SOAPAction** en-tête est déterminé par le **BTS. Opération** propriété de contexte. Par exemple, si cette propriété est définie au format XML suivant et le **BTS. Opération** est définie sur **Op1**, l’adaptateur d’envoi WCF utilise http://contoso.com/Svc/Op1 pour sortant **SOAPAction** en-tête.  
  
     `<BtsActionMapping>`  
  
     `<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" />`  
  
     `<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" />`  
  
     `</BtsActionMapping>`  
  
     Si les messages sortants proviennent d’un port d’orchestration, les instances d’orchestration définir dynamiquement le **BTS. Opération** propriété avec le nom de l’opération du port. Si les messages sortants sont acheminés avec le routage basé sur le contenu, vous pouvez définir le **BTS. Opération** propriété dans les composants de pipeline. Les ports générés par l’Assistant consommation de WCF BizTalk ont des opérations avec des noms qui correspondent à la **nom** les attributs dans le  **<BtsActionMapping>**  élément. Vous n’êtes pas obligé de définir explicitement la **BTS. Opération** propriété dans les orchestrations lorsque vous envoyez des messages via les ports qui ont été générées par l’Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des Orchestrations en tant que Services WCF](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)   
 [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des schémas en tant que Services WCF](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)