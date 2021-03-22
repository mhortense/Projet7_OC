{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "name": "README.ipynb",
      "provenance": [],
      "collapsed_sections": []
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "ruynTrREs23Q"
      },
      "source": [
        "# README\n",
        "\n",
        "Note méthodologique d'accompagnement pour décrire 4 points clefs du projet :\n",
        "\n",
        "- La méthodologie d'entraînement du modèle\n",
        "- La fonction coût, l'algorithme d'optimisation et la métrique d'évaluation\n",
        "- L’interprétabilité du modèle\n",
        "- Les limites et les améliorations possibles\n",
        "\n",
        "\n",
        "## La méthodologie d'entraînement du modèle\n",
        "\n",
        "Le modèle est entrainé et testé sur les donnéees du set test venant du fichier csv \"application_train.csv\".\n",
        "Une fois le modèle avec les perfomances optimales selectionné, il est aussi appliqué au fichier \"application_test.csv\".\n",
        "\n",
        "\n",
        "## La fonction coût, l'algorithme d'optimisation et la métrique d'évaluation\n",
        "\n",
        "**Fonction coût:**\n",
        "La fonction coût représente la fonction dont l'erreur est à réduire au maximal. Pour des modèles simples de régression linéaire, on peut considérer que la fonction coût est l'erreur quadratique.\n",
        "Ici, on considère que la fonction coût est l'inverse du score auc. Le but est d'avoir un espace sous la courbe roc maximal. \n",
        "\n",
        "**Algorithme d'optimisation:** \n",
        "Afin de réduire la fonction coût de manière optimale, nous avons optimisé le seuil de discrimination établit à partir des probabilités de prédiction de classification dans une catégorie ou l'autre (TARGET= 1 ou TARGET= 0). \n",
        "\n",
        "**Métriques d'évaluation:** \n",
        "Les modèles ont été comparé grâce à des métriques d'évaluation de la qualité d'une classification binaire:\n",
        "- Le score auc, représentant l'espace sous la courbe ROC. Cette courbe donne le taux de Vrais Positifs (fraction des positifs qui sont effectivement détectés) en fonction du taux de Faux Positifs (fraction des négatifs qui sont incorrectement détectés) $ \\frac{Vrais Positifs}  {Faux Positifs} $ ; \n",
        "- Le f-1 score, combine une mesure de la précision : $ \\frac{Vrais Positifs}  {(Vrais Positifs + Faux Positifs)} $ et du rappel : $ \\frac{Vrais Positifs} {(Vrais Positifs + Faux Négatifs)} $ ;\n",
        "- Le coefficient de corrélation de Matthew, prend en compte toutes les classes de la matrice de confusion (Vrais Positifs, Faux Positifs, Vrais Négatifs et Faux Négatifs) et est généralement considéré comme une mesure équilibrée qui peut être utilisée même si les classes sont de tailles très différentes. \n",
        "\n",
        "\n",
        "## L’interprétabilité du modèle\n",
        "\n",
        "Le score auc permet d'évaluer les performances du modèle et de minimiser les situations les moins acceptables pour la banque, c'est à dire les faux positifs. \n",
        "Ce score est la métrique qui a servit pour le calcul de la fonction coût et pour le calcul du seuil de discrimination dans l'algorithme d'optimisation. \n",
        "\n",
        "Le seuil d'éligibilité par le modèle choisi (XGBoostClassifier) est de 0.092. Si la probabilité d'avoir TARGET=1 est au dessus de ce seuil, le client devrait être éligible à un crédit.\n",
        "\n",
        "## Les limites et les améliorations possibles\n",
        "\n",
        "Le preprocessing des données pourrait être amelioré grâce à l'apport des connaissances métier par d'autres membres de l'équipe.\n",
        "Il semble d'ailleurs que les features les plus importantes pour la prédiction de l'attribution d'un crédit soit des variables pour lesquelles on a très peu d'informations (ex: EXT_SOURCE_2, EXT_SOURCE_3, FLAG_DOCUMENT_3).\n"
      ]
    }
  ]
}