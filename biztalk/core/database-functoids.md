---
title: "Fonctoids de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77bc9390-cdb5-42ff-8b28-6265c51c79fc
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b68a924fba60d4f0162e80dde0ab06b515765558
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="database-functoids"></a>Fonctoids de base de données
**Base de données** fonctoids extraient des données à partir d’une base de données pour une utilisation dans un message d’instance de sortie. 

## <a name="overview"></a>Vue d'ensemble
Voici une liste de la **base de données** fonctoids et comment vous pouvez les utiliser :  
  
-   **Recherche de la base de données.** Utilisez le **recherche de base de données** fonctoid pour extraire des informations à partir d’une base de données et les stocker en tant qu’un jeu d’enregistrements Microsoft ActiveX Data Objects .NET (ADO.NET). Ce fonctoid requiert quatre paramètres d'entrée dans l'ordre suivant :  
  
    -   Une valeur de recherche  
  
    -   Une chaîne de connexion à la base de données  
  
    -   Un nom de table  
  
    -   Un nom de colonne pour la valeur de recherche  
  
-   **Retour d’erreur.** Utilisez le **retour d’erreur** fonctoid pour capturer les informations d’erreur, tels que les échecs de connexion de base de données, qui se produisent pendant l’exécution. Ce fonctoid requiert un paramètre d’entrée : un lien à partir de la **recherche de base de données** fonctoid.  
  
-   **Message de format.** renvoie une chaîne formatée et localisée utilisant une substitution d'argument et, potentiellement, des références croisées d'ID et de valeurs.  
  
-   **Obtenir l’ID d’Application.** extrait un identificateur pour un objet d'application.  
  
-   **Obtenir la valeur de l’Application.** extrait une valeur d'application.  
  
-   **Obtenir l’ID courant :** extrait un identificateur pour un objet commun.  
  
-   **Obtenir la valeur courante.** extrait une valeur commune.  
  
-   **Supprimer l’ID d’Application.** Supprime une valeur d’application.  
  
-   **Définir l’ID courant** Permet de définir et renvoyer un identificateur pour un objet courant.  
  
-   **Extracteur de valeur.** Utilisez le **extracteur de valeur** fonctoid pour extraire des données à partir de la colonne spécifiée dans un jeu d’enregistrements renvoyé par le **recherche de base de données** fonctoid. Ce fonctoid requiert deux paramètres d’entrée : un lien vers le **recherche de base de données** fonctoid et un nom de colonne.  
  
 Sept de la **base de données** fonctoids : **formater Message, obtenir l’ID Application**, **obtenir la valeur Application**, **obtenir l’ID courant**, **Obtenir la valeur courante**, **supprimer l’identificateur d’Application**, et **définir l’ID courant**— sont **CrossReferencing** fonctoids. Ces fonctoids convertissent les ID et valeurs d'un message d'entrée en ID et valeurs requises dans le message de sortie. Pour plus d’informations, consultez **référence des fonctoids de base de données** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 

## <a name="example"></a>Exemple  
 L’exemple suivant utilise certaines le **base de données** fonctoids. Imaginez un grand détaillant dont les magasins sont répartis sur une zone géographique étendue. Pour suivre les magasins, le siège attribue à chaque magasin d’un code unique appelé un **StoreID**. En outre, le siège associe les informations suivantes à chaque **StoreID**:  
  
-   StoreName  
  
-   StoreAddress  
  
-   Ville  
  
-   PostalCode  
  
-   StorePhoneNumber  
  
-   StoreManager  
  
 Ces informations sont stockées dans une base de données et communiquées régulièrement aux partenaires commerciaux. L'ensemble des achats du détaillant sont effectués par le siège et non par les magasins. Lorsque le siège envoie un bon de commande aux partenaires commerciaux, en général, plusieurs magasins reçoivent les marchandises commandées à l'aide de cet unique bon de commande. Au lieu d’envoyer des informations de nom et l’adresse pour chaque magasin devant recevoir la marchandise, siège envoie simplement la **StoreID**. Pour insérer les informations de nom et l’adresse dans l’avis d’expédition avancée, le partenaire commercial utilise le **base de données** fonctoids insère automatiquement ces informations dans le message d’instance de sortie. La figure suivante montre comment un partenaire commercial peut mettre en œuvre le remplacement du StoreID dans un mappage.  
  
 ![Mapper les fonctoids de base de données différente affichant. ] (../core/media/origdbfunctoids.gif "origdbfunctoids")  
  
 Dans cette figure, le schéma source représente un bon de commande entrant, le schéma de destination un avis d'expédition avancée. Le **recherche de base de données** fonctoid Recherche l’enregistrement approprié dans la table de base de données appropriée. Le **extracteur de valeur** fonctoids extraient la colonne appropriée à partir de l’enregistrement de recherche. Le **retour d’erreur** fonctoid génère une chaîne contenant des informations sur l’erreur s’il existe des erreurs (telles que les échecs de connexion) en cours d’exécution.  
  
 Dans l’exemple précédent, le premier paramètre d’entrée est issu de la **StoreID** champ d’entrant bons de commande et les autres trois paramètres d’entrée sont des constantes configurées dans le **configurer \< Fonctoid > fonctoid** boîte de dialogue pour le **recherche de base de données** fonctoid. Il est possible de créer des liens à partir du schéma source afin de fournir des valeurs pour les quatre paramètres d'entrée.  
  
> [!NOTE]
>  * Vous ne pouvez pas utiliser certains types de données Microsoft SQL Server, tels que **texte**, **ntext**, et **image**, en tant que valeurs de recherche pour le **recherche de base de données** fonctoid. Le fonctoid requiert des types de données pouvant être représentés par une chaîne de texte.  
>
>  * S’il existe plusieurs enregistrements correspondant aux paramètres d’entrée de la **recherche de base de données** fonctoid, le **extracteur de valeur** fonctoid extrait des données uniquement à partir du premier enregistrement.  
>
>  * Dans les chaînes de connexion, utilisez l'authentification NT pour protéger les mots de passe par chiffrement.  

## <a name="available-functoids"></a>Fonctoids disponibles  
 Le **base de données** fonctoids sont : 

* Recherche dans la base de données
* Retour d'erreur
* Formater message
* Obtenir l'ID d'application
* Obtenir la valeur d'application
* Obtenir l'ID courant
* Obtenir la valeur courante
* Supprimer l'identificateur d'application
* Définir l'ID courant
* Extracteur de valeur

Pour plus d’informations sur ces functiods, consultez la **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

## <a name="see-also"></a>Voir aussi  
-  [Ajout de fonctoids de base à une carte](../core/how-to-add-basic-functoids-to-a-map.md)   
-  **Référence des fonctoids de base de données**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]