pipeline {
  agent any
  stages {
    stage('start et server') {
      steps {
        sh '''set -eo pipefail

virtualenv .env
source .env/bin/activate
pip install -U pip
pip install -r requirements.txt

python One_click_button/et_image_actions.py --action start_instance --rpm_build $RPM_BUILD_JOB_ID

pwd
env'''
        git(url: 'https://gitlab.cee.redhat.com/qgong/errata-qe-ci.git', branch: 'master', poll: true)
      }
    }
  }
}