---
title: "Installation des problèmes connus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2f80ff9-b37c-49f8-8250-fcf3cec4c0fc
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf4e9197d2b3c448b4fd9cc42c0cdeb929917061
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installation-known-issues"></a>Installation des problèmes connus
Des informations utiles qui peuvent vous aider à éviter les problèmes d’installation.  
  
## <a name="prerequisites-for-installing-btahl7"></a>Conditions préalables pour l’installation BTAHL7  
 Les conditions préalables pour l’installation [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] incluent les éléments suivants :  
  
-   Composants de base de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], y compris Enterprise Single Sign-On (SSO), de groupe et de Runtime, doit être configuré.  
  
-   L’utilisateur de l’installation et la configuration de BTAHL7 doit être membre du groupe Administrateurs de BizTalk et un membre du groupe Administrateurs sur le serveur SQL Server où sont stockées les données BTAHL7.
  
## <a name="sql-server-mixed-mode-not-supported"></a>En mode mixte SQL Server non prise en charge.  
Le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ne prend pas en charge SQL Server en mode mixte.  
  
## <a name="repair-does-not-work-from-uninstallchange"></a>La réparation ne fonctionne pas de désinstaller/modifier  
Si le contrôle d’accès utilisateur (UAC) est activé et que vous essayez de réparer votre installation en utilisant le panneau de configuration, la réparation échoue. 

Microsoft recommande que vous conservez le compte d’utilisateur activé.

 **Résolution**  
  
 Exécutez le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] setup.exe, puis sélectionnez **réparation**.  
  
## <a name="see-also"></a>Voir aussi  
[Installer ou mettre à niveau de Microsoft BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)