# Submission and demonstration checklist

Use this alongside the [course rubric](https://github.com/Nency-Ravaliya/devops-heros/blob/main/session21-python/GRADING.md) when collecting screenshots and preparing the demo. The linked repository did not include `student-guide.md` when checked on October 17, 2026; confirm the deadline, submission form and recording format with the instructor.

| Module | Points | Implementation | Required evidence |
|---|---:|---|---|
| M1 Application | 10 | `backend/app`, Alembic revision, React UI | Browser screenshot; create/read/update/delete ticket and PostgreSQL table |
| M2 Testing | 10 | `backend/tests`, `pytest.ini`; isolated test DB | `pytest -v` screenshot with passing results; successful PostgreSQL CI tests |
| M3 Git | 5 | Existing repository, root `.gitignore` | Repository URL with instructor access; at least 10 meaningful real commits and history screenshot |
| M4 Docker | 10 | Both Dockerfiles; Compose; non-root runtime UIDs | Successful build/stack logs and browser at localhost:3000 |
| M5 CI/CD | 15 | `.github/workflows/ci-cd.yml` | Green Actions run URL; GHCR package screenshots with full SHA tags; deployment update |
| M6 Security | 5 | Blocking Trivy scans on both images | Actual scan reports and screenshot; 2–3 sentence finding/clean-scan explanation |
| M7 Terraform | 15 | `terraform/*.tf`, tfvars example | Successful init/plan; AWS VPC + EKS screenshots; destroy completion |
| M8 Kubernetes/Helm | 15 | `helm/queuedesk`, `k8s` | Running backend/frontend with ≥2 replicas; Services, Helm release, Ingress browser screenshot |
| M9 Observability | 10 | `/metrics`, ServiceMonitor, monitoring values/dashboard | Metrics output, Prometheus targets UP, populated Grafana panel |
| M10 Presentation | 5 | README and runbooks | Live demo or recording following commit → pipeline → deployment |

## Evidence to collect

- [ ] Confirm public repository/instructor access and submit its URL.
- [ ] Obtain and review the missing student guide with the instructor.
- [ ] Capture original app UI on desktop and mobile.
- [ ] Run `cd backend && pytest -v`; capture the full summary.
- [ ] Capture `git log --oneline --graph` with at least ten meaningful commits.
- [ ] Capture `docker compose up --build` / healthy service output and http://localhost:3000.
- [ ] Capture successful Actions run URL, both Trivy reports and GHCR SHA tags.
- [ ] Write 2–3 sentences about the scan: which package had a finding, the affected and fixed versions, and what was changed. For a clean scan, explain what was checked and the result.
- [ ] Capture Terraform plan output and AWS VPC/subnets/EKS/node-group screenshots in your chosen region.
- [ ] Capture `kubectl get pods -n queuedesk`, `kubectl get svc -n queuedesk`, `helm list -n queuedesk`, Ingress and HPA output.
- [ ] Capture browser traffic through the ALB, backend `/metrics`, Prometheus Targets with both app endpoints UP, and a populated Grafana panel.
- [ ] Demonstrate a failure lab and record diagnosis, correction and recovery.
- [ ] Present live or record the demo, then destroy AWS resources and capture the successful destroy.

## Suggested 12-minute demonstration

1. **0:00–1:30:** Explain the support-task domain and architecture. Create a ticket, assign it, resolve it, filter the queue.
2. **1:30–3:00:** Show Swagger CRUD, PostgreSQL `tickets` table, migration and passing tests.
3. **3:00–5:30:** Make a small visible change. Commit and push. Explain test/build/Trivy gates and immutable SHA tags while the workflow runs.
4. **5:30–7:00:** Show Terraform VPC/private workers, EKS and node group. Explain NAT, IAM/OIDC and persistent EBS storage.
5. **7:00–8:30:** Show Helm release, migration Job, ready replicas, Services, Ingress and new image SHA after deployment.
6. **8:30–10:00:** Generate traffic; show Grafana, Prometheus and HPA. Report measured scaling behavior honestly.
7. **10:00–11:30:** Apply one isolated broken manifest, diagnose its events/selectors, repair and show recovery.
8. **11:30–12:00:** Explain limitations and cleanup. Submit destroy evidence after evaluation as instructed.
