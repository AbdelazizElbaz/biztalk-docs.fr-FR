---
title: "Générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff01e2b0-6480-427a-bc6d-6169e7d6e256
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 035f1263922a0c455662139ca112794e920e3848
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts"></a>Générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP
Vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou un contrat de service WCF (interface) ciblé sur les opérations sélectionnées sur les artefacts SAP. Vous pouvez également utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer la classe de client WCF ou le contrat de service WCF ; Toutefois, le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] expose les fonctionnalités de l’utilitaire de métadonnées ServiceModel via une interface de Microsoft Windows standard. Il fournit également des fonctionnalités de navigation et de recherche qui ne sont pas disponibles avec l’outil svcutil.exe et génère un fichier de configuration basé sur les propriétés de liaison que vous sélectionnez lorsque vous vous connectez au système SAP.  
  
## <a name="generating-a-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>Génération d’une classe de Client à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Procédez comme suit pour générer une classe de client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-generate-a-wcf-client-class"></a>Pour générer une classe de client WCF  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur votre projet, puis cliquez sur **ajouter une référence de Service de carte**.  
  
2.  Après le **ajouter une référence de Service de carte** boîte de dialogue s’ouvre, suivez les étapes de [obtenir les métadonnées pour les opérations de SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md) pour se connecter à un système SAP et de parcourir et de recherche pour les opérations. Pour créer une classe de client WCF pour les opérations que vous sélectionnez, assurez-vous que **Client (Outbound operations)** est sélectionné dans le **type de contrat Select** liste déroulante (il s’agit de la valeur par défaut).  
  
3.  Après avoir sélectionné toutes les opérations que vous souhaitez cibler, cliquez sur **OK** pour générer la classe de client WCF.  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ajoute deux fichiers à votre projet :  
  
-   **SAPBindingClient.cs**. Ce fichier contient le WCF client classe et assistance code généré pour les opérations que vous avez sélectionné.  
  
-   **App.config**. Ce fichier contient une configuration de liaison et les configurations de point de terminaison de client. Les paramètres sont basés sur les sélections effectuées lors de la configuration de la liaison et la connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier app.config. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier app.config, si nécessaire.  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un contrat de Service WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Lorsque vous utilisez le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour recevoir des IDOC, RFC et tRFCs à partir du système SAP, votre code fonctionne comme un service à l’adaptateur. Autrement dit, l’adaptateur reçoit l’artefact approprié à partir du système SAP et puis appelle une opération (entrante) sur votre code pour remettre l’artefact à votre application.  
  
 Vous devez, par conséquent, implémenter un service WCF qui peut recevoir cette opération entrante à partir de l’adaptateur. Pour ce faire, vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une interface .NET qui représente le contrat de service qui est visible par l’adaptateur pour l’opération. Cette interface .NET est également appelée un contrat de service WCF. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également une classe qui contient une implémentation d’un stub du service WCF. Puis, vous implémentez cette interface pour créer le service WCF que vous pouvez utiliser pour l’opération de réception.  
  
 Procédez comme suit pour générer un contrat de service WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-generate-a-wcf-service-contract"></a>Pour générer un contrat de service WCF  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur votre projet, puis cliquez sur **ajouter une référence de Service de carte**.  
  
2.  Après le **ajouter une référence de Service de carte** boîte de dialogue s’ouvre, suivez les étapes de [obtenir les métadonnées pour les opérations de SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md) pour se connecter à un système SAP et de parcourir et de recherche pour les opérations. Pour créer un contrat de service WCF pour les opérations que vous sélectionnez, assurez-vous que **Service (opérations entrantes)** est sélectionné dans le **type de contrat Select** liste déroulante.  
  
3.  Après avoir sélectionné toutes les opérations que vous souhaitez cibler, cliquez sur **OK** pour générer le contrat de service WCF.  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ajoute trois fichiers à votre projet :  
  
-   **SAPBindingInterface.cs**. Ce fichier contient le WCF généré service contrat (interface) et le code d’application d’assistance pour les opérations que vous avez sélectionné.  
  
-   **SAPBindingService.cs**. Ce fichier contient une classe de service WCF stub qui implémente l’interface définie dans SAPBindingInterface.cs. Vous pouvez implémenter la logique métier qui traite le document RFC, le tRFC ou IDOC directement dans les méthodes de cette classe.  
  
-   **App.config**. Ce fichier contient une configuration de liaison, des comportements de point de terminaison et configuration de point de terminaison de service qui sont basées sur les sélections effectuées lors de la configuration de la liaison et la connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier app.config. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier app.config, si nécessaire.  
  
> [!NOTE]
>  Vous n’êtes pas obligé de spécifier les paramètres de serveur RFC lorsque vous configurez l’URI de connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer le contrat de service WCF. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] récupère les métadonnées à partir du système SAP via une connexion cliente.  
  
## <a name="generate-a-wcf-client-class-or-a-wcf-service-contract-by-using-svcutilexe"></a>Générer une classe de Client WCF ou un contrat de Service WCF à l’aide de svcutil.exe  
 Vous pouvez utiliser svcutil.exe pour générer une classe de client WCF ou un contrat de service WCF pour votre application. Vous devez configurer svcutil.exe pour l’utiliser avec le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Pour plus d’informations sur la configuration et l’utilisation de svcutil.exe avec la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [à l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md).  
  
 SvcUtil.exe génère la classe de client WCF ou le contrat de service WCF dans un fichier de sortie. Le nom de fichier par défaut est output.cs. Vous devez inclure manuellement ce fichier dans votre [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet.  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)