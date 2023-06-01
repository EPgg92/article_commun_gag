# article_commun_gag

Écrivons tous au même endroit mais de manière organiser avec des reviews et un historique plus clair!

## Limitations du repos pour forcer les bonnes pratiques de review

Et oui pour éviter que chacun ne voit pas les changement passer il faut des règles de review 🙂

Voila ce qui est en place:

- Require a pull request before merging
  - Require at least 2 approvals
  - Dismiss stale pull request approvals when new commits are pushed
- Require conversation resolution before merging
- Allow force pushes (everyone)
- Allow deletions

### Commits

Essayez d'éviter les `git add * ; git commit -m "lol"`!
Comme ça on peut review commit par commit 😊
Merci !
