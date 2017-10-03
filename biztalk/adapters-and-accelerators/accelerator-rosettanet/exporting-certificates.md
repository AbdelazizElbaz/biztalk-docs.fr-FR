---
title: Exportation de certificats | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting certificates
- certificates, exporting
ms.assetid: edeeb300-19d6-44a8-b730-dcd15891cdf9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1898162b27956e4e527013ff765edf6aea440e9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exporting-certificates"></a>Exportation de certificats
Cette rubrique explique comment exporter un certificat à l'aide de l'Assistant Exportation du certificat. Utilisez cet Assistant pour exporter un certificat public ou un certificat privé.  
  
### <a name="to-export-a-partner-certificate"></a>Pour exporter un certificat de partenaire  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Développez **Certificats (Ordinateur local)**, développez **Autres personnes**, puis cliquez sur **Certificats**.  
  
3.  Dans le volet droit, cliquez avec le bouton droit sur le nom du certificat, pointez sur **Toutes les tâches**, puis cliquez sur **Exporter**.  
  
4.  Dans la page **Bienvenue dans l'Assistant Exportation du certificat** , cliquez sur **Suivant**.  
  
5.  Dans la page **Format du fichier d'exportation** , sélectionnez le format à utiliser pour le fichier. Il s'agit généralement du format x.509 binaire encodé DER pour exporter un fichier binaire, ou du format x.509 encodé Base 64 pour exporter un fichier Base 64.  
  
    > [!NOTE]
    >  L'encodage d'un certificat au format Base 64 vous permet d'utiliser le certificat sur un serveur UNIX.  
  
6.  Dans la page **Fichier à exporter** , cliquez sur **Parcourir**, recherchez l'emplacement de stockage du fichier, tapez le nom de ce dernier, cliquez sur **Suivant**, puis sur **Terminer**.  
  
### <a name="to-export-the-home-organization-certificate"></a>Pour exporter le certificat de l'organisation d'origine  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **runas/user :\<héberger service > mmc**, où \< *hostservice* > est le nom du service que vous avez associé le service hôte lorsque vous avez installé [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)], puis cliquez sur **OK** pour exécuter le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC) dans le contexte de la service de l’hôte.  
  
    > [!NOTE]
    >  Vous exécutez la commande **runas** pour emprunter l'identité du service hôte, ce qui est indispensable pour accéder au certificat de l'organisation d'origine.  
  
2.  Développez **Certificats - Utilisateur actuel**, développez **Personnel**, puis cliquez sur **Certificats**.  
  
3.  Dans le volet droit, cliquez avec le bouton droit sur le nom du certificat, pointez sur **Toutes les tâches**, puis cliquez sur **Exporter**.  
  
4.  Dans la page **Bienvenue dans l'Assistant Exportation du certificat** , cliquez sur **Suivant**.  
  
5.  Pour exporter la clé publique associée à la clé privée d'un certificat, laissez l'option **Non, ne pas exporter la clé privée** sélectionnée. Pour exporter la clé privée, sélectionnez **Oui, exporter la clé privée**.  
  
    > [!NOTE]
    >  Si vous sélectionnez **Oui, exporter la clé privée**, il est fortement recommandé de ne pas envoyer le fichier résultant à un partenaire.  
  
    > [!NOTE]
    >  L'option **Oui, exporter la clé privée** n'est pas disponible si vous n'avez pas rendu la clé privée exportable quand vous l'avez importée au préalable.  
  
6.  Dans la page **Format du fichier d'exportation** , sélectionnez le format à utiliser pour le fichier. Il s'agit généralement du format x.509 binaire encodé DER pour exporter un fichier binaire, ou du format x.509 encodé Base 64 pour exporter un fichier Base 64.  
  
    > [!NOTE]
    >  L'encodage d'un certificat au format Base 64 vous permet d'utiliser le certificat sur un serveur UNIX.  
  
7.  Dans la page **Fichier à exporter** , cliquez sur **Parcourir**, recherchez l'emplacement de stockage du fichier, tapez le nom de ce dernier, cliquez sur **Suivant**, puis sur **Terminer**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des certificats](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)