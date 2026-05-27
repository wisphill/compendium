  889  helm repo add authentik https://charts.goauthentik.io\nhelm repo update
  890  helm template authentik authentik/authentik
  891  helm template authentik authentik/authentik | grep image:
  892  helm template authentik authentik/authentik -f values.yaml | grep image: