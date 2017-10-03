---
title: Glossaire de BizTalk accelerator pour SWIFT dans BizTalk Server | Documents Microsoft
description: "Termes et définitions de connaître et d’apprendre à utiliser BizTalk Accelerator pour SWIFT de courantes"
ms.custom: 
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7331beb-f6a7-4eea-8b31-28f5d15666d0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1230b6b1578a4a3aa7c719df4dffb718b0c748e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="glossary"></a>Glossaire
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour SWIFT utilise la terminologie suivante et les définitions.  
  
## <a name="a"></a>Un  
 **assembleur**  
 A [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] composant de pipeline d’envoi qui est appelée lors de la phase d’assemblage du traitement du pipeline de sortie. En règle générale, un assembleur effectue le travail de la sérialisation d’un message sortant à partir de XML dans un format de fichier plat.  
  
 **assembly**  
 Le principal bloc de construction d’un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)] application. Il s’agit de l’unité de base de réutilisation, de contrôle de version, de sécurité et de déploiement. Il est une collection de fichiers qui s’affichent au programmeur une (DLL) unique-dynamic link library ou d’un fichier exécutable (EXE).  
  
 **cache de l’assembly**  
 Un cache de code au niveau de l’ordinateur utilisé pour le stockage des assemblys côte à côte. Il existe deux parties dans le cache. Le global assembly cache contient des assemblys installés explicitement pour être partagés entre plusieurs applications sur l’ordinateur. Le cache de téléchargement stocke le code téléchargé à partir d’Internet ou les sites intranet, l’application qui a déclenché le téléchargement afin que le code téléchargé pour le compte d’une application isolées ou de page n’affecte pas les autres applications.  
  
## <a name="b"></a>B  
 **Code identificateur de banque (BIC)**  
 Code utilisé pour identifier une institution financière, comme défini par SWIFT.  
  
 **Outil Éditeur des règles d’entreprise**  
 Outil basé sur l'interface utilisateur graphique permettant d'élaborer des stratégies.  
  
 **Moteur de règles d’entreprise (BRE)**  
 Moteur d'inférence d'exécution servant à évaluer les règles par rapport aux faits et à mettre en place des actions en fonction des résultats de l'analyse.  
  
## <a name="c"></a>C  
 **règle conditionnelle**  
 Une règle de spécification d’une relation entre les champs d’un type de message SWIFT. Les règles conditionnelles sont définies dans le Guide de mise en production de normes SWIFT.  
  
## <a name="d"></a>D  
 **désassembleur**  
 A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] composant de pipeline qui est appelée lors de la phase de désassemblage du traitement de pipeline entrant. En règle générale, un dissembler effectue le travail de l’analyse d’un message entrant à partir d’un format de fichier plat au format XML.  
  
## <a name="e"></a>E  
 **code d’erreur**  
 Code, composé d’une lettre suivie de deux chiffres, en indiquant une violation des règles pour un type de message donné.  
  
 **Extensible Markup Language (XML)**  
 Spécification développée par le World Wide Web Consortium (W3C) qui permet aux concepteurs de créer des balises personnalisées au-delà des capacités du code HTML standard. Alors que HTML utilise des balises prédéfinies pour décrire les éléments dans la page, le langage XML permet des étiquettes pour être définies par le développeur de la page. Les balises de n'importe quel élément de données, tel qu'un produit ou un montant dû, peuvent être utilisées pour des applications spécifiques. Les pages web peuvent ainsi fonctionner en tant qu'enregistrements de base de données.  
  
 **Feuille de style XSL (Extensible Language)**  
 Format de feuille de style pour les documents de Extensible Markup Language (XML). XSL est utilisé pour définir l’affichage des données XML de la même façon que feuilles de style en cascade (CSS) sont utilisées pour définir l’affichage du langage HTML (Hypertext Markup). [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]utilise XSL comme langage de conversion entre deux spécifications.  
  
## <a name="f"></a>F  
 **FIN**  
 Messages pour lesquels SWIFT a défini des schémas et des normes de validation dans SWIFT normes version Guide 2003 financiers.  
  
## <a name="g"></a>G  
 **cache d’assembly global (GAC)**  
 Cache de code au niveau de la machine qui stocke les assemblys installés spécialement pour être partagés entre de nombreuses applications sur l'ordinateur. Les applications déployées dans le global assembly cache doivent avoir un nom fort.  
  
## <a name="h"></a>H  
 **Protocole HTTP sécurisé (HTTPS)**  
 Protocole HTTP (Hypertext Transfer) à l’aide du protocole de chiffrement Secure Sockets Layer (SSL).  
  
## <a name="i"></a>I  
 **échange**  
 Un message complet, constitué de blocs ou de parties de message plus petites. Par exemple, un rapide de l’échange dans [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] est défini comme la concaténation d’une partie de l’en-tête SWIFT (SWIFT blocs 1, 2, 3), suivie d’une partie du corps SWIFT (SWIFT bloc 4), suivie d’une partie du code de fin SWIFT (SWIFT bloc 5).  
  
## <a name="m"></a>M  
 **carte**  
 Fichier XML qui définit les relations de correspondance entre les enregistrements et les champs de deux spécifications. Un mappage contient une feuille de style XSL (Extensible Language) feuille de style [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] utilise pour effectuer la transformation décrite dans le mappage. Vous créez des cartes dans le Mappeur BizTalk.  
  
 **type de message**  
 Un des formats de message définis dans le Guide de mise en production de normes SWIFT, tels que « Réception contre le paiement ». Types de messages sont souvent signalées par « MT » suivi d’un code à trois chiffres.  
  
## <a name="p"></a>P  
 **Identificateur de Transaction de paiement (PTI)**  
 Identificateur de transaction unique, fourni par le client d’origine, qui est attaché aux messages bancaire de paiement provenant des banques, tels que les messages de l’émission de paiement et avis de crédit.  
  
 **stratégie**  
 Collection gérée de règles d'entreprise.  
  
 **PTI**  
 Identificateur de Transaction de paiement.  
  
## <a name="r"></a>R  
 **règle**  
 Association de conditions et d'actions.  
  
 **ensemble de règles**  
 Groupe logique de règles similaires. Il peut être considéré comme un procédé de groupement/segmentation du moteur de règles.  
  
## <a name="s"></a>S  
 **schéma**  
 Définition de la structure d'un fichier XML. Un schéma contient des informations sur les propriétés concernant les enregistrements et les champs de la structure.  
  
 **Société de télécommunication financière Interbank (SWIFT) dans le monde entier**  
 Société de télécommunication financière de Interbank dans le monde entier. Une organisation qui fournit des services de messagerie pour les banques, -courtiers, gestionnaires et des infrastructures de marché paiements, finances, titres, le commerce et. SWIFT crée un traitement des données partagé dans le monde entier et liaison de communication et un langage commun pour les transactions financières internationales.  
  
 **spécification**  
 A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]-schéma XML spécifique. Spécifications sont créées dans l’Éditeur BizTalk et peuvent être basées sur des normes industrielles (par exemple, SWIFT, EDIFACT, X 12 et XML) ou sur des fichiers plats (délimités, positionnels, ou délimités et positionnels). Le Mappeur BizTalk utilise des spécifications, ouvertes sous forme de spécifications source et de destination, pour créer des mappages.  
  
 **nom fort**  
 Un nom qui se compose de l’identité d’un assembly : son simple nom textuel, numéro de version et des informations de culture (le cas échéant), auquel s’ajoutent une clé publique et une signature numérique générées sur l’assembly. Étant donné que le manifeste d’assembly contient des hachages pour tous les fichiers constituant l’implémentation de l’assembly, il est suffisant pour générer la signature numérique sur l’unique fichier dans l’assembly qui contient le manifeste d’assembly. Les assemblys portant le même nom fort doivent être identiques.  
  
 **Traitement direct (STP)**  
 Le traitement automatique d’un message sur plusieurs étapes, aucune intervention manuelle. Généralement appliquées pour le chemin d’accès de traitement à partir de la réception d’un message à partir de SWIFT au niveau d’une institution financière pour la validation de la transaction résultante dans les systèmes internes de l’institution financière ; ou, à partir de la réception d’une instruction externe ou une action dans une institution financière à la transmission des messages résultants via SWIFT ou d’autres infrastructures financières ; ou, à partir d’un système institution financière interne à la transmission d’un ou plusieurs messages SWIFT ou d’autres infrastructures financiers.  
  
 **Guides de mise en production de normes SWIFT (SRG)**  
 La publication rapide qui fournit les normes mis à jour et proposées pour l’ensemble des messages FIN. Il s’agit d’un ensemble de plusieurs volume de documents de définition de la disposition et les champs pour chaque type de message, les valeurs valides et les formats pour chaque champ, appliquées à chaque message, les règles de réseau et que toutes les règles d’utilisation ou les pratiques courantes. Cette publication de CD est disponible par le service d’abonnement de SWIFT.  
  
 **Système provient le code de fin (SYS)**  
 Un code de fin ajouté par le réseau rapide pour les messages remis à une institution financière, indiquant que le service FIN a généré le message. Diffusions, les réponses aux demandes des utilisateurs et les rapports sont des exemples.  
  
## <a name="u"></a>U  
 **Identificateur unique de remise (URI)**  
 Un identificateur généré par les participants au programme d’étape majeure de paiements RosettaNet pour synchroniser les échanges bancaire avec les échanges d’entreprise.  
  
## <a name="x"></a>X  
  
 **XML-Data Reduced (XDR)**  
 Langage plus ancien utilisé pour créer un schéma, qui identifie la structure et les contraintes d’un document XML donné. XML-Data Reduced fait référence au sous-ensemble de la spécification de schéma XML-Data qui a été mis à disposition dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] analyseur XML (MSXML) 3.0 et versions ultérieures. Il exécute les tâches de base de mêmes qu’une DTD, mais avec plus de puissance et flexibilité. Contrairement aux DTD, qui exige son propre langage et la syntaxe, XDR utilise la syntaxe XML sa langue. Contrairement à XSD, qui a ne été que récemment recommandé comme standard, XDR a été implémentée et mis à disposition par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] bien avant l’existence de XSD comme standard recommandé par le groupe de travail de schéma XML W3C.  
  
 **Définition de schéma XML (XSD)**  
 Langage proposé par le groupe de travail de schéma XML W3C pour une utilisation dans la définition de schémas. Les schémas sont utiles pour l’application de structure et/ou limiter les types de données qui peuvent être utilisées correctement dans d’autres documents XML. Définition de schéma XML fait référence à la norme entièrement spécifiée et actuellement recommandée pour une utilisation dans des schémas XML. Étant donné que la spécification de XSD a été finalisée que récemment, prend en charge pour qu’il a été apportée uniquement disponible avec la version de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] XML Core Services (MSXML) 4.0. Il exécute les tâches de base de mêmes qu’une DTD, mais avec plus de puissance et flexibilité. Contrairement aux DTD, qui exige son propre langage et la syntaxe, XSD utilise la syntaxe XML sa langue. XSD ressemble à étroitement et étend les fonctionnalités de XDR. Le W3C recommande l’utilisation de XSD comme standard pour définir les schémas XML.