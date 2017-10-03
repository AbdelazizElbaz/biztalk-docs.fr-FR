---
title: Installation de certificats pour les adaptateurs WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tools, Certificates Management Console
- certificates, installing [WCF adapters]
- certificates, Certificates Management Console
- certificates, WCF adapters
- WCF adapters, send locations
- receive locations, WCF adapters
- send locations, WCF adapters
- WCF adapters, receive locations
- WCF adapters, certificates
ms.assetid: 04dc065f-a6e8-4359-8696-2a3de24d531d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 654e5300c253bbf4cede2113c9282b6a2f02862c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-certificates-for-the-wcf-adapters"></a>Installation de certificats pour les adaptateurs WCF
Les adaptateurs WCF font appel à des certificats numériques d'infrastructure à clé publique (PKI) pour le chiffrement et le déchiffrement de messages, pour la signature et la vérification (non-répudiation) de messages, ainsi que pour l'authentification du client. Cette rubrique présente divers scénarios d'utilisation des certificats ainsi que des instructions sur les options de configuration en matière d'utilisation des certificats numériques avec les adaptateurs WCF.  
  
## <a name="certificate-usage-scenarios-for-the-wcf-receive-locations"></a>Scénarios d'utilisation des certificats pour les emplacements de réception WCF  
 Le tableau suivant illustre l'installation des certificats pour les emplacements de réception WCF.  
  
|Utilisation des certificats|Contexte utilisateur|Emplacement du magasin de certificats|Type de certificat|Moment d'installation des certificats|  
|-----------------------|------------------|--------------------------------|----------------------|--------------------------------------|  
|Déchiffrement et signature en fonction des paramètres de sécurité de l'emplacement de réception.|Compte utilisé par l'instance d'hôte associée au gestionnaire de réception|Ouvrez une session sur chaque ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui hébergera les emplacements de réception en tant que chaque compte de service d’instance hôte et importer le certificat de service pour le **utilisateur actuel \ personnel (My)** stocker.|Propre certificat privé|Spécifiez la valeur de la **certificat de Service - empreinte** propriété dans les configurations suivantes :<br /><br /> -La **mode de sécurité** emplacement de réception de la propriété de WCF-BasicHttp est définie sur **Message**.<br />-La **type d’informations d’identification du client du Transport** emplacement de réception de la propriété de WCF-BasicHttp est définie sur **certificat** pour le **TransportCredentialOnly** mode de sécurité.<br />-La **type d’informations d’identification de client de Message** emplacement de réception de la propriété de WCF-WSHttp est définie sur **aucun**, **certificat**, ou **nom d’utilisateur** pour le **Message** mode de sécurité.<br />-La **type d’informations d’identification du client du Transport** emplacement de réception de la propriété de WCF-NetTcp est définie sur **aucun** ou **certificat** pour la **Transport**mode de sécurité.<br />-La **type d’informations d’identification de client de Message** emplacement de réception de la propriété de WCF-NetTcp est définie sur **aucun**, **nom d’utilisateur**, ou **certificat** pour le **Message** mode de sécurité.<br />-La **type d’informations d’identification de client de Message** emplacement de réception de la propriété de WCF-NetTcp est définie sur **Windows**, **nom d’utilisateur**, ou **certificat**pour la **TransportWithMessageCredential** mode de sécurité.<br />-La **mode de sécurité** de WCF-NetMsmq est définie sur **Message** ou **les deux**.|  
|Authentification du client|Néant|Connectez-vous à chaque ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui hébergera les emplacements de réception en tant qu'administrateurs, puis importez la chaîne de certificats de l'autorité de certification des certificats X.509 du client dans le magasin de certificats des autorités de certification racines de confiance de cet ordinateur, de manière à ce que les clients puissent être authentifiés auprès de cet emplacement de réception.|Chaîne de certificats de l'autorité de certification des certificats X.509 du client|Installez la chaîne de certificats de l'autorité de certification X.509 du client dans le magasin de certificats des autorités de certification racines de confiance dans les configurations suivantes :<br /><br /> -La **type d’informations d’identification de client de Message** ou **type d’informations d’identification du client du Transport** emplacement de réception de la propriété de WCF-BasicHttp est définie sur **certificat**.<br />-La **type d’informations d’identification de client de Message** ou **type d’informations d’identification du client du Transport** emplacement de réception de la propriété de WCF-WSHttp est définie sur **certificat**.<br />-La **type d’informations d’identification de client de Message** ou **type d’informations d’identification du client du Transport** emplacement de réception de la propriété de WCF-NetTcp est définie sur **certificat**.<br />-La **type d’informations d’identification de client de Message** ou **mode d’authentification MSMQ** emplacement de réception de la propriété de WCF-NetMsmq est définie sur **certificat**.|  
  
> [!NOTE]
>  Étant donné que WCF standard adaptateurs de réception utilisent le [ChainTrust](http://go.microsoft.com/fwlink/?LinkId=88960) mode pour valider les certificats clients, vous devez installer la chaîne de certificats d’autorité de certification pour les certificats X.509 du client. Vous pouvez utiliser WCF-Custom ou les adaptateurs WCF-CustomIsolated à cange ce comportement par défaut.  
  
> [!NOTE]
>  Pour les adaptateurs de réception WCF isolés, vous devez faire correspondre le compte d'utilisateur avec une instance d'hôte isolée et le pool d'applications correspondant. Pour plus d’informations sur les hôtes BizTalk isolé, consultez [activation des Services Web](../core/enabling-web-services.md).  
  
> [!NOTE]
>  Le WCF-Custom et WCF-CustomIsolated recevoir des emplacements, le contexte de l’utilisateur, l’emplacement du magasin de certificats, et le type de certificat pour les certificats à installer le **serviceCredentials** et  **clientCredentials** paramètres d’élément de comportement.  
  
> [!NOTE]
>  Si l’emplacement de réception utilise l’élément de certificat pour le **identité du point de terminaison** propriété, vous devez également installer le certificat de l’identité du service publié dans le magasin de certificats spécifié dans le  **Identité du point de terminaison** propriété.  
  
> [!NOTE]
>  Plutôt que de vous connecter à l'ordinateur à l'aide du compte de service ou du compte d'administrateur de l'instance d'hôte, vous pouvez faire appel à la commande Exécuter en tant que, avec les comptes appropriés.  
  
## <a name="certificate-usage-scenarios-for-the-wcf-send-ports"></a>Scénarios d'utilisation des certificats pour les ports d'envoi WCF  
 Le tableau suivant illustre l'installation des certificats pour les ports d'envoi WCF.  
  
|Utilisation des certificats|Contexte utilisateur|Emplacement du magasin de certificats|Type de certificat|Moment d'installation des certificats|  
|-----------------------|------------------|--------------------------------|----------------------|--------------------------------------|  
|Authentification du client|Compte utilisé par l'instance d'hôte associée au port d'envoi|Ouvrez une session sur chaque ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui hébergera les ports d’envoi en tant que chaque compte de service d’instance hôte et importer le certificat client à le **utilisateur actuel \ personnel (My)** stocker.|Propre certificat privé|Spécifiez la valeur de la **certificat Client - empreinte** propriété dans les configurations suivantes :<br /><br /> -La **type d’informations d’identification de client de Message** ou **type d’informations d’identification du client du Transport** du port d’envoi WCF-BasicHttp est définie sur **certificat**.<br />-La **type d’informations d’identification de client de Message** ou **type d’informations d’identification du client du Transport** du port d’envoi WCF-WSHttp est définie sur **certificat**.<br />-La **type d’informations d’identification de client de Message** ou **type d’informations d’identification du client du Transport** du port d’envoi WCF-NetTcp est définie sur **certificat**.<br />-La **type d’informations d’identification de client de Message** ou **mode d’authentification MSMQ** du port d’envoi WCF-NetMsmq est définie sur **certificat**.|  
|Authentification du service, vérification de signature et chiffrement selon les paramètres de sécurité du port d'envoi|Néant|Ouvrez une session sur chaque ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui hébergera les ports d’envoi en tant qu’administrateurs et importer le certificat de service pour le **ordinateur Local \ autres personnes (AddressBook)** stocker. Vous devez également installer la chaîne de certificats de l'autorité de certification des certificats de service dans le magasin de certificats des autorités de certification racines de confiance de l'ordinateur.|: Certificat public du Service<br />-La chaîne de certificat d’autorité de certification pour le certificat de service|Spécifiez la valeur de la **certificat de Service - empreinte** propriété dans les configurations suivantes :<br /><br /> -La **type d’informations d’identification de client de Message** ou **type d’informations d’identification du client du Transport** du port d’envoi WCF-BasicHttp est définie sur **certificat**.<br />-La **type d’informations d’identification de client de Message** du port d’envoi WCF-WSHttp est définie sur **aucun**, **nom d’utilisateur**, ou **certificat** lors de la **Négocier les informations d’identification du service** option est désactivée.<br />-La **mode de sécurité** d’envoi WCF-NetMsmq port est défini sur **Message** ou **les deux**.|  
|Authentification du service, vérification de signature et chiffrement selon les paramètres de sécurité du port d'envoi|Néant|Connectez-vous à chaque ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui hébergera les ports d'envoi en tant qu'administrateurs, puis importez la chaîne de certificats de l'autorité de certification des certificats X.509 du client dans le magasin de certificats des autorités de certification racines de confiance de cet ordinateur, de manière à ce que le service puisse être authentifié auprès de ce port d'envoi.|Chaîne de certificats de l'autorité de certification du certificat de service|Si vous ne spécifiez pas explicitement le certificat de service pour le **certificat de Service - empreinte** propriété, installez la chaîne de certificats d’autorité de certification pour le service X.509 des certificats aux autorités de Certification racine approuvées magasin de certificats dans les configurations suivantes :<br /><br /> -La **mode de sécurité** d’envoi WCF-BasicHttp port est défini sur **Transport** ou **TransportWithMessageCredential**.<br />-La **mode de sécurité** d’envoi WCF-WSHttp port est défini sur **Transport** ou **TransportWithMessageCredential**.<br />-La **mode de sécurité** d’envoi WCF-NetTcp port est défini sur **TransportWithMessageCredential**.<br />-La **type d’informations d’identification du client du Transport** du port d’envoi WCF-NetTcp est définie sur **aucun** ou **certificat**.<br />-La **type d’informations d’identification de client de Message** du port d’envoi WCF-NetTcp est définie sur **aucun**, **nom d’utilisateur**, ou **certificat**.|  
  
> [!NOTE]
>  Étant donné que les adaptateurs d’envoi WCF standard le [ChainTrust](http://go.microsoft.com/fwlink/?LinkId=88960) mode pour valider les certificats de service, vous devez installer la chaîne de certificats d’autorité de certification pour les certificats X.509 de service. Pour modifier le comportement par défaut, vous pouvez utiliser l'adaptateur WCF-Custom ou WCF-CustomIsolated.  
  
> [!NOTE]
>  Envoient le WCF-Custom et WCF-CustomIsolated des ports, le contexte de l’utilisateur, l’emplacement du magasin de certificats, et le type de certificat pour les certificats à installer le **serviceCredentials** et  **clientCredentials** paramètres d’élément de comportement.  
  
> [!NOTE]
>  Si le port d’envoi utilise l’élément de certificat pour le **identité du point de terminaison** propriété, vous devez également installer le certificat de l’identité du service attendu dans le magasin de certificats spécifié dans le **point de terminaison Identité** propriété.  
  
> [!NOTE]
>  Plutôt que de vous connecter à l'ordinateur à l'aide du compte de service ou du compte d'administrateur de l'instance d'hôte, vous pouvez faire appel à la commande Exécuter en tant que, avec les comptes appropriés.  
  
## <a name="displaying-the-certificates-management-console"></a>Affichage de la console de gestion des certificats  
 Pour afficher l'interface de la console de gestion des certificats pour Ordinateur local et Utilisateur actuel, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **MMC**, puis cliquez sur **OK** pour ouvrir la Console de gestion de Microsoft.  
  
2.  Sur le **fichier** menu, cliquez sur **ajouter/supprimer un composant logiciel enfichable** pour afficher les **ajouter/supprimer un composant logiciel enfichable** boîte de dialogue.  
  
3.  Cliquez sur **ajouter** pour afficher les **ajouter Standalone Snap-in** boîte de dialogue.  
  
4.  Sélectionnez **certificats** dans la liste des composants logiciel enfichables, puis cliquez sur **ajouter**.  
  
5.  Sélectionnez **compte d’ordinateur**, cliquez sur **suivant**, puis cliquez sur **Terminer**. L'interface de la console de gestion des certificats est alors ajoutée pour Ordinateur local.  
  
6.  Vérifiez que **certificats** est toujours sélectionné dans la liste des composants logiciel enfichables, puis cliquez sur **ajouter** à nouveau.  
  
7.  Sélectionnez **mon compte d’utilisateur**, puis cliquez sur **Terminer**. L'interface de la console de gestion des certificats est alors ajoutée pour Utilisateur actuel.  
  
    > [!NOTE]
    >  La console de gestion des certificats s'affiche pour le compte avec lequel vous êtes actuellement connecté. Pour importer des certificats dans le magasin Personnel d'un compte de service, vous devez d'abord ouvrir une session avec les informations d'identification de ce compte.  
  
8.  Cliquez sur **fermer** dans les **Standalone Snap-in** boîte de dialogue.  
  
9. Cliquez sur **OK** dans les **ajouter/supprimer un composant logiciel enfichable** boîte de dialogue.