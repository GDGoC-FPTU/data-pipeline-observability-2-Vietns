# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-XXXX  
**Name:** Vietns  
**Date:** 2026-06-10

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Du lieu da duoc validate nen chi con record hop le; category duoc chuan hoa va khong co gia am/rong. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Agent bi anh huong boi outlier rat lon va du lieu chua duoc lam sach. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai voi Garbage Data vi no tin truc tiep vao bang du lieu dau vao ma khong co buoc kiem tra chat luong. File garbage co duplicate ID, gia sai kieu du lieu nhu "ten dollars", category/null value thieu, va mot outlier rat lon la Nuclear Reactor voi gia 999999. Logic cua agent chi loc category electronics roi chon san pham co price cao nhat, nen outlier lap tuc tro thanh "best choice" du khong hop ly trong bai toan san pham thong thuong. Khi du lieu sach, cac record loi da bi loai, category dong nhat hon va price co y nghia hon, nen cau tra loi on dinh va dang tin cay hon. Dieu nay cho thay prompt tot khong the bu dap hoan toan cho nguon du lieu bi nhiem ban.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y. Prompt co the huong dan agent cach tra loi, nhung neu du lieu dau vao sai, trung lap, thieu hoac co outlier cuc doan thi agent van dua ra ket qua sai. Pipeline ETL giup lam sach va chuan hoa du lieu truoc khi agent su dung, nen chat luong du lieu la nen tang quan trong cua cau tra loi dung.
