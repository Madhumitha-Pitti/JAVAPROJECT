node {
   def mvnHome
  stage('Prepare') {
      git url: 'https://github.com/chethan-22/javacode.git', branch: 'main'
      mvnHome = tool 'maven'
   }
  stage ('Code Quality') {
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore sonar:sonar"
  }

  stage ('Clean') {
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean"
  }
  stage ('Validate') {
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore validate"
  }
  stage ('Compile') {
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore compile"
  }
  stage ('Test') {
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore test -t"
  }
  stage ('Package') {
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore package"
  }
  stage ('Verify') {
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore verify"
  }
  stage ('Install') {
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore install"
  }
  stage ('Deliver & Deployment') {
      sh 'curl -u admin:redhat@123 -T target/**.war "http://20.16.22.39:8080/manager/text/deploy?path=/chethan&update=true"'
  }
  stage ('SmokeTest') {
      sh 'curl --retry-delay 10 --retry 5 "http://20.16.22.39:8080/chethan"'
  }
}
