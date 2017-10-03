---
title: "Liste de vérification : Installation et configuration des certificats | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76a8f8f6-8d79-4caf-8fba-8cbcb251d461
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e675a60967b5ee34c40f1711f256aff76362d2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-installing-and-configuring-certificates"></a>Liste de vérification : Installation et configuration des certificats
Cette rubrique décrit les étapes de configuration des certificats à utiliser avec BizTalk Server.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Évaluer vos besoins de certificat et à revenir à un accord avec votre partenaire commercial sur vos responsabilités mutuelles en ce qui concerne les certificats.|Section « Évaluer et planifier l’utilisation de certificats » dans [meilleures pratiques pour la gestion des certificats](~/technical-guides/best-practices-for-managing-certificates2.md)|  
|Si vous utilisez la clé privée, demander une paire de clés publique-privée pour les signatures numériques à partir de l’autorité de certification (CA) et envoyer la clé publique à votre partenaire commercial.<br /><br /> Si vous utilisez la clé publique, votre demande de partenaire commercial une paire de clés publique-privée pour les signatures numériques à partir de l’autorité de certification et vous envoyer la clé publique.|[Comment installer des certificats de BizTalk Server](~/technical-guides/how-to-install-certificates-for-biztalk-server.md)|  
|Installez la clé privée ou publique dans le magasin de certificats approprié et votre partenaire commercial faire de même.|-   [Comment installer des certificats de BizTalk Server](~/technical-guides/how-to-install-certificates-for-biztalk-server.md)<br />-Section « Installer les certificats » [meilleures pratiques pour la gestion des certificats](~/technical-guides/best-practices-for-managing-certificates2.md)|  
|Si vous utilisez le certificat pour les messages MIME/SMIME, configurer BizTalk Server pour utiliser le certificat.|-   [Configuration des certificats pour MIME ou Messages SMIME](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)<br />-Section « Configurer BizTalk Server à utiliser des certificats pour MIME/SMIME » [meilleures pratiques pour la gestion des certificats](~/technical-guides/best-practices-for-managing-certificates2.md)|  
|(Facultatif) Si vous utilisez le certificat avec un adaptateur, configurez la carte pour utiliser le certificat.|-   [Configuration des certificats avec les adaptateurs](~/technical-guides/configuring-certificates-with-adapters.md)<br />-Section « Configurer un adaptateur BizTalk pour utiliser des certificats » [meilleures pratiques pour la gestion des certificats](~/technical-guides/best-practices-for-managing-certificates2.md)|  
|(Facultatif) Si vous utilisez le certificat pour effectuer la résolution de tiers, configurez le tiers pour utiliser le certificat.|[Comment configurer des certificats pour la résolution du tiers](~/technical-guides/how-to-configure-certificates-for-party-resolution.md)|  
|(Facultatif) Si vous exportez le certificat à partir d’un groupe BizTalk vers un autre, ajouter le certificat à une application BizTalk ; Exporter l’application dans un fichier .msi ; puis importer l’application dans un autre groupe BizTalk.|-   [Comment configurer des certificats pour la résolution du tiers](~/technical-guides/how-to-configure-certificates-for-party-resolution.md)<br />-   [Comment exporter une Application vers un fichier .msi](~/technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-   [Comment importer une Application à partir d’un fichier .msi](~/technical-guides/how-to-import-an-application-from-an-msi-file.md)<br />-Section « Exportation d’un certificat à partir d’un groupe BizTalk vers un autre » de [meilleures pratiques pour la gestion des certificats](~/technical-guides/best-practices-for-managing-certificates2.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques pour la gestion des certificats](~/technical-guides/best-practices-for-managing-certificates2.md)   
 [Problèmes connus avec les certificats dans BizTalk Server](~/technical-guides/known-issues-with-certificates-in-biztalk-server.md)