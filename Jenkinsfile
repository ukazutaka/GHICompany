#!/usr/bin/env groovy

pipeline {
    environment {
        PATH = "/product/project/customers:$PATH"
        CUSTOMERROOT = "/product/project/customers"
        NFSROOT = "/nfs"
    }    
    agent {
        docker { 
            image 'hrishioa/oyente' 
            args '-v /product/project/customers/ABCCompany/:/ABCCompany -w /ABCCompany'
            reuseNode true   
               }
    }

    stages {
        stage('Test') {
            steps {
                sh 'python $CUSTOMERROOT/ABCCompany/oyente.py $CUSTOMERROOT/ABCCompany/greeter.sol > /nfs/`date "+%Y%m%d_%H%M%S"`.json'
            }
        }
    }
}
