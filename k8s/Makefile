context:
	kubectl config use-context docker-desktop

build:
	cd ..; docker build -f ./Globomantics.Api/Dockerfile -t tmather99/globomantics_api:latest .
	cd ..; docker build -f ./Globomantics.Core/Dockerfile -t tmather99/globomantics_ui:latest .
	cd ..; docker build -f ./Globomantics.IdentityServer/Dockerfile -t tmather99/globomantics_is4:latest .
	cd ..; docker build -f ./sql/sql.Dockerfile -t tmather99/globomantics_database:latest .

push:
	docker push tmather99/globomantics_api:latest
	docker push tmather99/globomantics_ui:latest
	docker push tmather99/globomantics_is4:latest
	docker push tmather99/globomantics_database:latest

dashboard:
	kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
	kubectl apply -f https://gist.githubusercontent.com/dahlsailrunner/bbd453f3bb6259b66c08a70d0908283f/raw/5727723217e2df4b65d8933adf04d009cfb0fe3f/local-dashboard-account.yml

nginx:
	kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.4.0/deploy/static/provider/cloud/deploy.yaml

ingress:
	kubectl apply -f globo-ingress.yml
	kubectl apply -f kd-ingress.yml

echo:
	kubectl apply -f echo-server.yml

up:
	kubectl apply -f globo-seq.yml
	kubectl apply -f globo-smtp.yml
	kubectl apply -f globo-sql.yml
	kubectl apply -f globo-is4.configmap.yml
	kubectl apply -f globo-is4.yml
	kubectl apply -f globo-ui.configmap.yml
	kubectl apply -f globo-ui.yml
	kubectl apply -f globo-api.configmap.yml
	kubectl apply -f globo-api.yml

down:
	kubectl delete -f globo-seq.yml
	kubectl delete -f globo-smtp.yml
	kubectl delete -f globo-sql.yml
	kubectl delete -f globo-is4.configmap.yml
	kubectl delete -f globo-is4.yml
	kubectl delete -f globo-ui.configmap.yml
	kubectl delete -f globo-ui.yml
	kubectl delete -f globo-api.configmap.yml
	kubectl delete -f globo-api.yml

rm_echo:
	kubectl delete -f echo-server.yml

rm_dashboard:
	kubectl delete -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
	kubectl delete -f https://gist.githubusercontent.com/dahlsailrunner/bbd453f3bb6259b66c08a70d0908283f/raw/5727723217e2df4b65d8933adf04d009cfb0fe3f/local-dashboard-account.yml

rm_nginx:
	kubectl delete -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.4.0/deploy/static/provider/cloud/deploy.yaml

rm_ingress:
	kubectl delete -f globo-ingress.yml
	kubectl delete -f kd-ingress.yml

config:
	kubectl create secret generic globoconn-secrets \
                --from-literal=ConnectionStrings__IS4DbConnection="Server=globosql-service;Database=GlobomanticsIdSrv;User Id=sa;Password=Th@nhy99;MultipleActiveResultSets=true;" \
                --from-literal=ConnectionStrings__GlobomanticsDb="Server=globosql-service;Database=Globomantics;User Id=globo_dbuser;Password=Th@nhy99;MultipleActiveResultSets=true;"
	kubectl create secret tls idlocal-tls --key="certs/id-local.key" --cert="certs/id-local.crt"
	kubectl create secret tls seqlocal-tls --key="certs/seq-local.key" --cert="certs/seq-local.crt"
	kubectl create secret tls wwwlocal-tls --key="certs/www-local.key" --cert="certs/www-local.crt"
	kubectl create secret tls echolocal-tls --key="certs/echo-local.key" --cert="certs/echo-local.crt"
	kubectl -n kubernetes-dashboard create secret tls kdlocal-tls --key="certs/kd-local.key" --cert="certs/kd-local.crt"

rm_config:
	kubectl delete secret globoconn-secrets
	kubectl delete secret idlocal-tls
	kubectl delete secret seqlocal-tls
	kubectl delete secret wwwlocal-tls
	kubectl delete secret echolocal-tls
	kubectl delete secret -n kubernetes-dashboard kdlocal-tls

get_token:
	kubectl -n kubernetes-dashboard create token admin-user
