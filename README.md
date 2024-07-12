# fastapi
this is for test header, query parameter and path parameter with istio 

## push ke ghcr lewat cli

1. login (-p atau --password, -u atau --username). password adalah token (PAT)

template

        docker login ghcr.io -u USERNAME -p YOUR_PAT

kasus

        docker login ghcr.io -u practice-course -p ********

2. build image

template nya

        docker build -t ghcr.io/USERNAME/REPO_NAME/IMAGE_NAME:TAG .

kasus

        docker build -t ghcr.io/practice-course/fastapi/querypathparams:latest .

3. push

template

        docker push ghcr.io/USERNAME/REPO_NAME/IMAGE_NAME:TAG

kasus

        docker push ghcr.io/practice-course/fastapi/querypathparams:latest

4. melihat semua image

        docker image ls

kita juga bisa melihat image di repo bagian package

5. menguji

        docker run nama-image

        docker run ghcr.io/practice-course/fastapi/querypathparams:latest

## CI dengan github action
### buat secret 
digunakan untuk menyimpan hal yang rahasia seperti token (PAT)

1. di repo pilih settings
2. pilih secrets and variables 
3. pilih actions
4. pilih kotak secrets (bukan variable2)
5. pada bagian repository secrets pilih New repository secret
6. pada bagian Name isi 

            GH_PAT

merupakan token (PAT)

bagian secret copy kan token (PAT) nya

7. pilih add secret

### buat ci
#### otomatis dan edit
1. pada repo pilih actions 
2. pilih simple (akan membuat ci otomatis/template nya) 
3. pada file yaml masukkan perintah ci
#### buat dari awal 
1. di root repo buat .github/workflows/
2. didalam folder workflows buat file manifes yang akan melakukan ci (kasus ini build dan push image ke ghcr).

misal kita buat file publish-ghcr.yaml
3. lakukan commit dan push ke git repo
4. di repo pilih Actions dan lihat github sedang menjalankan ci

