---
title: "Configuration d’une Solution CIDX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CIDX, process configuration
- creating, CIDX solutions
- CIDX, connecting to Elemica network
- agreements, CIDX
- process configuration, CIDX
- CIDX, agreements
- PIPs, importing for CIDX
- CIDX, PIPs
- CIDX, creating solutions
- CIDX, importing PIPs
- PIPs, CIDX
ms.assetid: 7f1f159f-3b09-4efd-907b-9a75f7f3ecd1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab617efc701551f1d5bcbae2a292676cc4f33251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-up-a-cidx-solution"></a>Configuration d’une Solution CIDX
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prend en charge pour l’échange de messages XML de CIDX (Chemical Industry Data Exchange) (les normes de CIDX chem versions 2.0 et 3.0). Cette rubrique décrit comment configurer une solution CIDX en procédant comme suit :  
  
-   Configuration d’une configuration de processus  
  
-   Configuration d’un accord  
  
-   Application d’un PIP  
  
-   Importation d'un PIP basé sur XSD  
  
-   Connexion au réseau Elemica  
  
## <a name="setting-up-a-cidx-process-configuration"></a>Installation d’une Configuration de processus CIDX  
 Pour configurer un échange de messages chem CIDX, vous devez créer une configuration de processus qui a les propriétés suivantes :  
  
-   **Standard** propriété dans les paramètres de configuration de processus la valeur **CIDX**  
  
-   **Est la seule Action** propriété dans les paramètres de configuration de processus la valeur **True**  
  
-   **Accord de 0 a 1** propriété dans l’accord de partenariat commercial, la valeur **aucune 0 a 1**  
  
 Pour plus d’informations, consultez [paramètre des CIDX chem échange de messages](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md).  
  
## <a name="creating-a-cidx-agreement"></a>Création d’un accord CIDX  
 Pour configurer un échange de messages chem CIDX, vous devez créer un accord qui a les propriétés suivantes :  
  
-   **Version de RNIF** propriété dans les paramètres d’accord définie sur **V01.10.00**  
  
-   **Accord de 0 a 1** propriété dans les paramètres d’accord défini sur **aucune 0 a 1**  
  
 Pour plus d’informations, consultez [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
## <a name="applying-a-pip-for-cidx"></a>Application d’une adresse PIP pour CIDX  
 Pour appliquer une adresse PIP à une implémentation CIDX, définissez la **Standard** propriété dans le profil de configuration de processus pour **CIDX**. Une fois que vous avez terminé, vous serez en mesure d’entrer des valeurs pour le **standard Message**, **version Standard**, et **ID de liaison de charge utile**. Vous pouvez trouver ces valeurs dans la spécification de chem CIDX normes.  
  
## <a name="importing-an-xsd-based-pip-for-cidx"></a>L’importation d’un PIP basé sur XSD pour CIDX  
 Pour importer un PIP basé sur XSD pour CIDX, vous devez télécharger le fichier ZIP de l’adresse du PIP à partir de CIDX.org à l’adresse [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361). Procédez comme décrite dans la procédure d’importation [l’importation d’un PIP basé sur XSD](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md).  
  
## <a name="connecting-to-the-elemica-network"></a>Connexion au réseau Elemica  
 Vous pouvez personnaliser [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] pour se connecter à Elemica à l’aide de fichiers de projet dans le Pack de connectivité Elemica. Vous pouvez télécharger le Pack de connectivité à partir de [http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195). Pour plus d’informations, consultez le livre blanc « Connexion au réseau Elemica avec BizTalk Accelerator pour RosettaNet 3.0 » sur MSDN à l’adresse [http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539).  
  
> [!NOTE]
>  Les informations contenues dans le livre blanc « Connexion au réseau Elemica avec BizTalk Accelerator pour RosettaNet 3.0 » sont valides pour [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge CIDX](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)   
 [Normes de messagerie CIDX](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md)   
 [Paramètre des CIDX chem échange de messages](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)   
 [Création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)   
 [L’importation d’un PIP basé sur XSD](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)