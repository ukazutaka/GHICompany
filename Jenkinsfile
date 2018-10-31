#!/usr/bin/env groovy

pipeline {
    environment {
        PATH = "/product/project/customers:$PATH"
        CUSTOMERROOT = "/product/project/customers"
        NFSROOT = "/nfs"
    }    
    agent {
        docker { 
            image 'mythril/myth' 
            args '-v /product/project/customers/GHICompany/:/GHICompany -w /GHICompany'
            reuseNode true   
               }
    }
    stages {
        stage('Tests') {
            steps {
                sh 'docker exec -v $(pwd):/tmp mythril/myth -x TGContract.sol > /nfs/`date "+%Y%m%d_%H%M%S"`.json'
            }
        }
    }
    
}
