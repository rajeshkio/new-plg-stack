issue with prometheus server in crashloop
https://github.com/helm/charts/issues/15742

I solved this problem with the below way.

kubectl edit deploy prometheus-server -n prometheus

from

      securityContext:
        fsGroup: 65534
        runAsGroup: 65534
        runAsNonRoot: true
        runAsUser: 65534
to

  securityContext:
    fsGroup: 0
    runAsGroup: 0
    runAsUser: 0
honestly, I am not sure this change won't cause another problem. but now it works
