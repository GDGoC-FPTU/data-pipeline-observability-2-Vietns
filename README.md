[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9agbb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112904&assignment_repo_type=AssignmentRepo)

# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** vietnguyen29403@gmail.com
**Name:** Nguyen Si Viet

---

## Mo ta

Bai lab nay xay dung mot ETL pipeline don gian bang Python. Pipeline doc du lieu san pham tu `raw_data.json`, validate va loai bo record khong hop le, transform du lieu bang cach tinh `discounted_price`, chuan hoa `category` sang Title Case, them timestamp `processed_at`, sau do load ket qua ra `processed_data.csv`.

---

## Cach chay

### Prerequisites

```bash
pip install pandas pytest
```

### Chay ETL Pipeline

```bash
python solution.py
```

Ket qua mong doi: file `processed_data.csv` duoc tao ra. Voi du lieu mau, pipeline extract 5 records, giu lai 3 records hop le va loai 2 records loi.

### Chay Agent Simulation va Stress Test

```bash
python generate_garbage.py
python -c "from agent_simulation import simulate_agent_response; print(simulate_agent_response('What is the best electronic product?', 'processed_data.csv'))"
python -c "from agent_simulation import simulate_agent_response; print(simulate_agent_response('What is the best electronic product?', 'garbage_data.csv'))"
```

---

## Cau truc thu muc

```text
solution.py              # ETL Pipeline script
raw_data.json            # Du lieu dau vao
processed_data.csv       # Output cua pipeline
garbage_data.csv         # Du lieu rac cho stress test
experiment_report.md     # Bao cao thi nghiem
README.md                # File huong dan nay
```

---

## Ket qua

Pipeline da xu ly thanh cong du lieu mau:

- 5 records extracted tu `raw_data.json`
- 3 records valid duoc giu lai
- 2 records invalid bi loai do `price <= 0` hoac `category` rong
- Output co cac cot `discounted_price` va `processed_at`

Stress test cho thay clean data giup agent chon Laptop hop ly, trong khi garbage data lam agent chon Nuclear Reactor do outlier gia 999999.
