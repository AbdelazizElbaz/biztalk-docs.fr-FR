---
title: "Générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7ffd857-a177-423a-ae83-685d11b7aec6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc7fb7dc0df1c2cbf4c4f8b1118cba07df6c7231
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-oracle-e-business-suite-solution-artifacts"></a>Générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite
Vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou un contrat de service WCF (interface) ciblé sur les opérations sélectionnées sur les artefacts d’Oracle E-Business Suite. Vous pouvez également utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer la classe de client WCF ou le contrat de service WCF ; Toutefois, le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] expose les fonctionnalités de l’utilitaire de métadonnées ServiceModel via une interface de Microsoft Windows standard. Il fournit également des fonctionnalités de navigation et de recherche qui ne sont pas disponibles avec l’outil svcutil.exe, et génère un fichier de configuration basé sur les propriétés de liaison que vous sélectionnez lorsque vous vous connectez à Oracle E-Business Suite.  
  
## <a name="generating-a-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>Génération d’une classe de Client à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Procédez comme suit pour générer une classe de client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-generate-a-wcf-client-class"></a>Pour générer une classe de client WCF  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur votre projet, puis cliquez sur **ajouter une référence de Service de carte**.  
  
2.  Après le **ajouter une référence de Service de carte** boîte de dialogue s’ouvre, suivez les étapes de [récupérer des métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) pour se connecter à Oracle E-Business Suite et Parcourir et rechercher des opérations. Pour créer une classe de client WCF pour les opérations que vous sélectionnez, assurez-vous que **Client (Outbound operations)** est sélectionné dans le **type de contrat Select** liste déroulante (il s’agit de la valeur par défaut).  
  
3.  Après avoir sélectionné toutes les opérations que vous souhaitez cibler, cliquez sur **OK** pour générer la classe de client WCF.  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ajoute deux fichiers à votre projet :  
  
-   **OracleEBSBindingClient.cs**. Ce fichier contient le WCF client classe et assistance code généré pour les opérations que vous avez sélectionné.  
  
-   **App.config**. Ce fichier contient une configuration de liaison et les configurations de point de terminaison de client. Ces configurations sont basées sur les sélections effectuées lors de la configuration de la liaison et la connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier app.config. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier app.config, si nécessaire.  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un contrat de Service WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 L’adaptateur expose les opérations entrantes pour permettre d’Oracle E-Business Suite envoyer des messages à un client de carte. Pour ces opérations, vous devez générer un contrat de service WCF. Cette section fournit des informations sur la génération d’un contrat de service pour les opérations entrantes exposées par l’adaptateur.  
  
 Procédez comme suit pour générer un contrat de service WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-generate-a-wcf-service-contract-for-inbound-operations"></a>Pour générer un contrat de service WCF pour les opérations entrantes  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur votre projet, puis cliquez sur **ajouter une référence de Service de carte**.  
  
2.  Après le **ajouter une référence de Service de carte** boîte de dialogue s’ouvre, suivez les étapes de [récupérer des métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) pour se connecter à Oracle E-Business Suite. Il existe plusieurs propriétés de liaison et une propriété URI que vous pouvez définir lorsque vous vous connectez à Oracle E-Business Suite.  
  
3.  Après vous être connecté à Oracle E-Business Suite, sélectionnez **Service (opérations entrantes)** à partir de la **type de contrat Select** liste déroulante.  
  
4.  Dans le **sélectionner une catégorie** zone, accédez à l’opération de trafic entrante pour lequel vous souhaitez générer le contrat de service. Par exemple, pour **Notification** opération, cliquez sur le nœud racine (**/**), sélectionnez **Notification** à partir de la **catégories disponibles et opérations** zone, puis cliquez sur **ajouter**. Pour obtenir des instructions sur la façon de rechercher les opérations entrantes, consultez [Parcourir, rechercher et récupérer des métadonnées pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
5.  Pour générer le contrat de service WCF pour l’opération, cliquez sur **OK**.  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ajoute trois fichiers à votre projet :  
  
-   **OracleEBSBindingInterface.cs**. Ce fichier contient le WCF généré contrat (interface) et le code d’application d’assistance pour l’opération entrante de service.  
  
-   **OracleEBSBindingService.cs**. Ce fichier contient une classe qui implémente l’interface définie dans OracleDBBindingInterface.cs. Vous pouvez implémenter la logique métier qui traite les enregistrements retournés par l’opération entrante.  
  
-   **App.config**. Ce fichier contient une configuration de liaison, des comportements de point de terminaison et configuration de point de terminaison de service qui sont basées sur les sélections effectuées lors de la configuration de la liaison et la connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier app.config. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier app.config, si nécessaire.  
  
## <a name="using-svcutilexe-to-generate-a-wcf-client-class-or-a-wcf-service-contract"></a>À l’aide de svcutil.exe pour générer une classe de Client WCF ou un contrat de Service WCF  
 Vous pouvez utiliser svcutil.exe pour générer une classe de client WCF ou une interface de service WCF pour votre application. Vous devez configurer svcutil.exe pour l’utiliser avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
 SvcUtil.exe génère la classe de client WCF ou le contrat de service WCF dans un fichier de sortie. Le nom de fichier par défaut est output.cs. Vous devez inclure manuellement ce fichier dans votre [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet. Pour plus d’informations sur svcutil.exe, consultez [http://go.microsoft.com/fwlink/?LinkId=139432](http://go.microsoft.com/fwlink/?LinkId=139432).