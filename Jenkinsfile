pipeline {
	agent any
	stages {
		stage("generate the test case") {
			steps {
				sh "g++ generate.cpp -o generate"
				sh "chmod u=x generate"
				sh ./generate
			}
		}
		stage("run the search engine") {
			steps {
				sh( returnStdout: false, script: """#!/bin/sh
                    echo gg!!
                    """.stripIndent()
                )
			}
		}
		stage("compare the results") {
			steps {
				sh if cmp -s RES.txt OUT.txt ; then echo SUCCESS ; else exit 1 ; fi
			}
		}
	}
}