---
title: "Configuration des documents informatisés (EDIFACT) de liste | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b03ace75-70bf-47c9-9a94-df813d7cab1e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f6b4d9a5aae6c8758d3a6d4f46d18f9a820fabd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-transaction-set-list-edifact"></a>Configuration de la liste des documents informatisés (EDIFACT)
[!INCLUDE[prague](../includes/prague-md.md)] permet de définir la liste des documents informatisés qui doivent toujours être inclus ou exclus lors du traitement d'un échange EDI. Cette section fournit des instructions sur la création de la liste des documents informatisés.  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-a-transaction-set-list"></a>Pour configurer la liste des documents informatisés  
  
1.  Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **liste des documents informatisés**.  
  
3.  Sélectionnez **prise en charge les documents informatisés de la liste** option si vous souhaitez créer une liste des documents informatisés qui doivent toujours être traités.  
  
    > [!NOTE]
    >  Utilisez cette option si vous recevez habituellement des échanges avec des types de transactions spécifiques, par exemple APERAK. Dans ce cas, ajoutez ce type de transactions à la liste pour que les transactions des autres types ne soient pas traitées.  
  
4.  Sélectionnez **exclure les documents informatisés dans la liste** option si vous souhaitez créer une liste des documents informatisés qui ne doit pas être traité.  
  
    > [!NOTE]
    >  Utilisez cette option si vous recevez habituellement des échanges avec divers types de transactions. Dans ce cas, vous ajoutez ces types de transactions à la liste pour laquelle vous n'obtenez aucun document informatisé.  
  
5.  Cliquez sur la cellule vide dans le **UNH2.1** colonne et à partir de la liste déroulante, sélectionnez le type que vous souhaitez prendre en charge ou exclure informatisé.  
  
6.  Pour supprimer un type de transaction dans la liste, sélectionnez la ligne pour le type de transaction, puis cliquez sur **supprimer**.  
  
7.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des documents informatisés (EDIFACT) de paramètres](../core/configuring-transaction-set-settings-edifact.md)