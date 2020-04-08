node {
  stage("Checkout"){
    git branch: "master",
    credentialsId: 'github',
    url: "git@github.ancestry.com:Ancestry/${env.REPO}.git"
  }
  stage("Git Tag"){
       sh """
          if [ ! -z "$GIT_REPO" ]; 
          then git clone --depth 1 --branch "$gitTag" "$GIT_REPO" tag && { cd tag || exit 1 ; } && 
          echo "Tagging git commit $env.BUILD_NUMBER with environment $ENV" && 
          { git tag -a -f "$ENV" $gitTag -m "Deployed to $ENV" && 
          git push -f --tags ; { cd .. || exit 1 ; } && 
          rm -rf tag ; } 
          fi
          """
  }
}
