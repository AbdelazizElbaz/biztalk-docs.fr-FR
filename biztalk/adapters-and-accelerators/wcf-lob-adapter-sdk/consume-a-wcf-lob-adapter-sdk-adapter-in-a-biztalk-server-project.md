---
title: Utiliser un adaptateur WCF LOB Adapter SDK dans un projet BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 041f14cc-d00f-450d-b1e9-40a3e423c510
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84f81d23b56c2631879f366e6fe502840408a0d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="consume-a-wcf-lob-adapter-sdk-adapter-in-a-biztalk-server-project"></a>Utiliser un adaptateur WCF LOB Adapter SDK dans un projet BizTalk Server
Cette rubrique décrit comment utiliser un adaptateur créé à l’aide de la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].  
  
> [!NOTE]
>  Pour pouvoir utiliser le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], vous devez installer le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] outils sur le même ordinateur qui héberge [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 
## <a name="use-the-consume-adapter-service-add-in"></a>Utilisez le Consume Adapter Service Add-in  
 
  
1.  Ouvrez votre application .NET dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **projet** volet, avec le bouton droit votre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] de projet, puis choisissez **ajouter**&#124; **Ajouter les éléments générés** &#124; **Consume Adapter Service**.  
  
3.  Dans la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] , sélectionnez une liaison de la carte.  
  
4.  Cliquez sur **configurer** pour configurer l’URI de connexion pour la liaison de la carte sélectionnée et fournir toutes les informations d’identification, les propriétés d’URI et les propriétés de liaison. La configuration requise réelle varie en fonction de la liaison de la carte sélectionnée.  
  
5.  Cliquez sur **OK** lorsque vous avez configuré l’URI.  
  
6.  Cliquez sur **Se connecter**. Si l’URI de connexion est valide et les informations d’identification de client (le cas échéant) sont acceptées, la **catégorie** volet doit être rempli avec les catégories et les opérations fournies par l’adaptateur.  
  
7.  Si l’adaptateur prend en charge la recherche, le champ de recherche sera actif. Sinon, vous pouvez filtrer par type de contrat et Explorer les types et les opérations en cliquant sur les nœuds dans le **catégorie** volet.  
  
8.  Cliquez sur **OK** pour générer les artefacts de proxy. Le nombre d’artefacts varie en fonction du type de contrat :  
  
    |Type de contrat|Artefact| Description||  
    |-------------------|--------------|-----------------|-|  
    |Sortant|Schémas XML|Contient les schémas pour les types sélectionnés et les opérations.||  
    |Sortant||Informations de liaison de port XML d’envoi WCF-Custom|Contient la configuration XML pour le port d’envoi WCF-Custom.|  
    |Trafic entrant|Schémas XML|Contient les schémas pour les types sélectionnés et les opérations.||  
    |Trafic entrant||Informations de liaison de port XML de réception WCF-Custom|Contient le fichier XML de configuration pour le port de réception WCF-Custom.|  
  
9. Vous pouvez maintenant utiliser des fichiers de schéma XML dans votre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application.  
  
## <a name="deploy-the-biztalk-server-project"></a>Déployer le projet BizTalk Server  
  
1.  Ouvrez **Administration de BizTalk Server.**  
  
2.  Importez les fichiers XML de liaison de port pour créer les ports physiques. Avec le bouton droit de votre application sous le **Applications** groupe, sélectionnez **importer les liaisons**, puis accédez à et sélectionnez les informations de liaison de port approprié ou les fichiers XML.  
  
3.  Mapper les ports logiques définis dans votre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestrations aux ports physiques nouvellement créés.  
  
4.  Cliquez sur **Orchestrations** sous votre application, cliquez sur l’orchestration à inscrire, puis cliquez sur **Enlist**.  
  
5.  Cliquez sur **Orchestrations** sous votre application, cliquez sur l’orchestration à inscrire, puis cliquez sur **Démarrer**.  
  
6.  Cliquez sur votre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, puis sur **Démarrer**.  
  
## <a name="generate-multiple-schemas"></a>Générer plusieurs schémas  
 Si vous utilisez l’Assistant consommer de Service d’adaptateur pour générer plusieurs schémas, un ou plusieurs éléments peuvent être dupliqués dans les schémas, ce qui entraîne un échec de la compilation pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projet. Vous pouvez éviter cela en sélectionnant le **générer le Type de schéma Unique** case à cocher pour vous assurer que les types de schéma sont générés avec des espaces de noms uniques.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser un adaptateur créé à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)