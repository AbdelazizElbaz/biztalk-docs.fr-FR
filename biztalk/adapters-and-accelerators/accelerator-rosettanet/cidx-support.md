---
title: Prise en charge CIDX | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CIDX, procedures
- CIDX, about CIDX
- CIDX, Elemica Exchange Server Provider (ESP)
- CIDX, PIPs
- CIDX
- Elemica Exchange Server Provider (ESP)
- procedures [CIDX]
- PIPs, CIDX
ms.assetid: 58b75ad3-f6b9-47c0-8dbf-506a3eaf010b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 224d2b50d132efa67e1cfc24dda2df77fa7d29e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cidx-support"></a>Prise en charge CIDX
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prend en charge l’échange de messages XML de CIDX (Chemical Industry Data Exchange). [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]prend en charge les normes CIDX chem versions 2.0 et 3.0, qui utilisent tous deux le Framework RNIF (RosettaNet Implementation) 1.1.  
  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus publics simples asynchrones (prise en charge des messages d’action unique et double action) consommer et acheminer du contenu de service CIDX.  
  
 Pour un contrat basé sur un PIP CIDX, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] validera les éléments suivants dans un message :  
  
-   Version de RNIF 1.1 uniquement  
  
-   Aucun 0 a 1  
  
-   Une seule Action  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]vous empêcheront pas de paramètre de la `Standard` propriété pour une configuration de processus à « CIDX », une fois que vous avez défini le `0A1 agreement` propriété pour un contrat qui utilise ce profil à « 0 a 1 » (qui n’est pas pris en charge pour CIDX). [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]n’effectue pas la validation de champ croisé susceptibles d’empêcher cela.  
  
## <a name="applying-a-pip-to-a-cidx-implementation"></a>Application d’une adresse PIP à une implémentation CIDX  
 Pour appliquer une adresse PIP à une implémentation CIDX, définissez la `Standard` propriété dans le profil de configuration de processus pour **CIDX**. Une fois que vous avez terminé, vous serez en mesure d’entrer des valeurs pour le Message standard, version Standard et ID de liaison de charge utile. Vous pouvez trouver ces valeurs dans la spécification de chem CIDX normes.  
  
## <a name="connecting-to-the-elemica-network"></a>Connexion au réseau Elemica  
 Vous pouvez activer une installation de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] pour se connecter à la Elemica [!INCLUDE[btsExchangeSvrNoVersion](../../includes/btsexchangesvrnoversion-md.md)] fournisseur (ESP). Vous pouvez utiliser le réseau Elemica pour l’achat de produits chimiques-secteur, la vente et la gestion de chaîne d’approvisionnement à l’aide de l’échange de messages CIDX.  
  
 Vous personnalisez [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] pour se connecter à Elemica à l’aide de fichiers de projet dans le Pack de connectivité Elemica. Vous pouvez télécharger le Pack de connectivité à partir de [http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195). Pour plus d’informations, consultez le livre blanc « Connexion au réseau Elemica avec BizTalk Accelerator pour RosettaNet 3.0 » sur MSDN à l’adresse [http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539).  
  
> [!NOTE]
>  Les informations contenues dans le livre blanc « Connexion au réseau Elemica avec BizTalk Accelerator pour RosettaNet 3.0 » sont valides pour [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)].  
  
## <a name="cidx-procedures"></a>Procédures CIDX  
 Les sections suivantes décrivent comment configurer l’échange de messages CIDX :  
  
-   [Paramètre des CIDX chem échange de messages](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)  
  
-   [Création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)  
  
-   [L’importation d’un PIP basé sur XSD](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator for RosettaNet ajoutée à BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [Normes de messagerie CIDX](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md)