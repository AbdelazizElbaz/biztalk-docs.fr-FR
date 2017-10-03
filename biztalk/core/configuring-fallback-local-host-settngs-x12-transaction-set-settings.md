---
title: "Configuration Settngs de secours de l’hôte Local (paramètres X12-Transaction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68511199-a7ed-45b3-807d-70378b2c6ebb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fa9e1fcc8bf1764a16142d38058e14878341fdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-local-host-settngs-x12-transaction-set-settings"></a>Configuration des paramètres de secours de l'hôte local (X12 - Paramètres de documents informatisés)
Pour traiter un échange entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit déterminer le schéma dont il a besoin pour le traitement et la validation de l'échange. Pour ce faire, il doit déterminer l'espace de noms cible associé au schéma, ainsi que le schéma à utiliser. Dans cette page de propriétés de secours, vous indiquez l'espace de noms cible de secours. Comment [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine le schéma est décrit dans [résolution de l’accord, détection de schéma et l’autorisation pour les Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).  
  
> [!NOTE]
>  Cette rubrique s'applique également aux paramètres liés à HIPAA.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a>Pour configurer les paramètres de l'hôte local des documents informatisés  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.  
  
2.  Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres des documents informatisés** , cliquez sur **paramètres d’hôte Local** .  
  
3.  Sélectionnez **conversion implicite de base 10 de valeur numérique de format décimal** pour convertir un nombre EDI spécifié au format Nn en une valeur numérique de base 10 dans le fichier XML intermédiaire dans BizTalk Server.  
  
    > [!NOTE]
    >  Une fois la conversion effectuée, la validation de la longueur du fichier XML intermédiaire peut échouer. Cela peut se produire car la valeur numérique en base 10 contient une virgule, ce qui la rend plus longue que le format Nn. Vous pouvez résoudre ce problème en ajoutant une valeur de **1** à la valeur de longueur minimale/maximale.  
  
4.  Sélectionnez **créer des balises XML vides pour les séparateurs de fin** pour que l’expéditeur des échanges inclue des balises XML vides pour les séparateurs de fin.  
  
5.  Pour **cible Namespace**, entrez (ou sélectionnez dans la liste déroulante) l’espace de noms cible qui [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise pour déterminer le schéma pour traiter le message reçu avec.  
  
6.  Cliquez sur **appliquer** pour accepter les modifications, ou cliquez sur **OK** pour entrer et valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration X12 définir les propriétés de l’accord de secours pour la Transaction paramètres](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)