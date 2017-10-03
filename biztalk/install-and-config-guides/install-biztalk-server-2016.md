---
title: Installer BizTalk Server 2016 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f5ac913-0734-45b2-8e25-1db146d81858
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f89aa7599040a2cc6c50f11b70c2751fcf2df1ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-biztalk-server-2016"></a>Installation de BizTalk Server 2016
Installez BizTalk Server sur un seul serveur.

## <a name="before-you-get-started"></a>Avant de commencer

* **Administrateur système** – Lorsque vous installez SQL Server, le programme d’installation accorde automatiquement des droits d’administrateur système à votre compte de connexion. Comme ces droits sont également requis pour installer BizTalk Server, effectuez l’une des opérations suivantes :
  * Utilisez le compte utilisé lors de l'installation de SQL Server.
  * Accordez des droits d’administrateur système au compte de connexion.
  * Confirmez que le compte de connexion est membre du groupe Administrateurs local.
* **Noms de comptes** – Dans la mesure du possible, utilisez les noms de comptes par défaut. Le programme d’installation de BizTalk Server entre automatiquement les comptes par défaut. Si le domaine contient plusieurs groupes BizTalk Server, changez les noms des comptes afin d’éviter les conflits. Si vous modifiez les noms, BizTalk Server ne prend en charge que le format *Nom de domaine NetBIOS\utilisateur* pour les comptes de service et les groupes Windows.
* **Noms de comptes avec le service web de gestion BAM** – BizTalk Server ne prend pas en charge les comptes intégrés ni les comptes sans mot de passe pour l’utilisateur de service web de gestion BAM. Le service web accède à la base de données BizTalk Server et ces comptes peuvent suggérer une menace pour la sécurité.

    > [!NOTE] 
    > Même si la configuration de BizTalk Server avec ces types de comptes réussit, le service web de gestion BAM échoue. Des comptes intégrés ou des comptes sans mot de passe peuvent être utilisés pour le pool d'applications BAM.

* **BizTalk Assembly Viewer** – Non pris en charge sur une plateforme 64 bits. 
* **Installation et désinstallation** – La désinstallation de BizTalk Server nécessite la suppression manuelle des bases de données BizTalk Server. Si vous installez BizTalk Server comme développeur ou évaluateur, utilisez une machine virtuelle. Si vous avez besoin de réinstaller, vous pouvez facilement restaurer la machine virtuelle sans avoir à désinstaller et à supprimer les bases de données.
* **Ordinateurs 32 bits et 64 bits** – L’installation de BizTalk Server sur des ordinateurs 32 bits et 64 bits présente quelques différences. La procédure d'installation et de configuration couvre les ordinateurs 32 bits et 64 bits. Les différences éventuelles sont signalées.
* **Groupes de travail** – L’installation et la configuration de BizTalk Server dans l’environnement de groupe de travail sur un seul ordinateur sont prises en charge. Les fonctionnalités et composants de SQL Server et BizTalk Server sont installés et configurés sur le même ordinateur.


## <a name="install-biztalk-server"></a>Installer BizTalk Server
1. Fermez tous les programmes ouverts. Exécutez le programme d’installation de BizTalk Server comme administrateur.
2. Sélectionnez **Installer Microsoft BizTalk Server 2016**.
3. Entrez votre **nom d’utilisateur**, votre **organisation** et votre clé de produit. Sélectionnez **Suivant**.
4. Acceptez le contrat de licence et sélectionnez **Suivant**.
5. Acceptez de participer au Programme d’amélioration du produit et sélectionnez **Suivant**.
6. Choisissez les composants à installer :

    ![bts2016install_components](../install-and-config-guides/media/bts2016install-components.gif)
  
    Veillez à sélectionner **Logiciels complémentaires**. Vous pouvez également modifier l’emplacement d’installation : 
  
    ![bts2016install_additional](../install-and-config-guides/media/bts2016install-additional.gif)

    Sélectionnez **Suivant**.   
  
 7. Selon les composants que vous choisissez, certains prérequis supplémentaires peuvent s’appliquer, tels qu’ADOMD.NET. Le programme d’installation peut installer automatiquement toute la configuration requise redistribuable pour vous. Parmi les options, citons :
* **Installer manuellement la configuration requise redistribuable** : L’Assistant Installation se ferme pour que vous puissiez installer manuellement les prérequis manquants.
* **Installer automatiquement la configuration requise redistribuable à partir du Web** : paramètre par défaut. Nécessite un accès Internet.
* **Télécharger le fichier CAB de la configuration requise redistribuable** : Télécharge un fichier CAB, que vous pouvez installer ultérieurement.
* **Installer automatiquement la configuration requise redistribuable à partir d’un fichier CAB** : Si vous avez téléchargé les fichiers CAB, vous pouvez sélectionner cette option pour utiliser ces fichiers CAB. 

  Sélectionnez **Suivant**.
  
8. Passez en revue la page Résumé. Pour apporter des modifications, sélectionnez **Précédent** pour cocher ou décocher des composants. 

     Pour activer la connexion automatique après un redémarrage système, sélectionnez **Définir** et entrez le compte de connexion. Ceci est possible uniquement pendant l’installation de BizTalk. Une fois le programme d’installation terminé, ce paramètre est désactivé. 

    Sélectionnez **Installer**.
  
9. Pour configurer BizTalk maintenant, cochez **Lancer la configuration de BizTalk Server**. Si vous ne voulez pas configurer BizTalk maintenant, décochez cette option et sélectionnez **Terminer** pour fermer l’Assistant Installation. 

Un fichier journal d’installation est généré dans un dossier temporaire, similaire à : `C:\Users\*username*\AppData\Local\Setup(011217 xxxxxx).htm`
  
## <a name="check-the-installation"></a>Vérification de l’installation

* BizTalk Server est répertorié dans **Programmes et fonctionnalités**.
* La clé de Registre `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0` répertorie la version de BizTalk Server, le chemin d’installation, l’édition et d’autres détails.
* Administration de BizTalk Server, Configuration de BizTalk Server et d’autres composants sont répertoriés dans vos applications. 

## <a name="next-step"></a>Étape suivante
[Configuration de BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)