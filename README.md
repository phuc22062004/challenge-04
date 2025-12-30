
## Hướng Dẫn Chạy Dự Án

### Yêu Cầu Hệ Thống

Trước khi bắt đầu, bạn cần cài đặt các công cụ sau:

- **[Node.js (>= v20.18.3)](https://nodejs.org/en/download/)** - Runtime môi trường JavaScript
- **[Yarn](https://classic.yarnpkg.com/en/docs/install/)** - Package manager (v1 hoặc v2+)
- **[Git](https://git-scm.com/downloads)** - Hệ thống quản lý phiên bản

### Cài Đặt Dự Án

**Cài đặt dependencies**:
```bash
yarn install
```

### Chạy Dự Án Từng Bước

Dự án này sử dụng kiến trúc monorepo với 3 thành phần chính cần chạy song song:

#### Bước 1: Khởi động Local Blockchain Network

Mở **terminal thứ nhất** và chạy lệnh sau để khởi động mạng blockchain local (Hardhat Network):

```bash
yarn chain
```

**Giữ terminal này mở**.

#### Bước 2: Deploy Smart Contracts

Mở **terminal thứ hai** (giữ terminal thứ nhất đang chạy) và chạy lệnh deploy:

```bash
yarn deploy
```

#### Bước 3: Khởi động Frontend

Mở **terminal thứ ba** (giữ cả 2 terminal trước đang chạy) và chạy lệnh:

```bash
yarn start
```

#### Bước 4: Truy cập ứng dụng

Mở trình duyệt và truy cập:
```
http://localhost:3000
```

### Deploy Lên Testnet (Sepolia/Optimism Sepolia)

1. **Cấu hình network** trong `packages/hardhat/hardhat.config.ts`:
   - Đặt `defaultNetwork` thành `sepolia` hoặc `optimismSepolia`

2. **Tạo và cấu hình tài khoản deployer**:
```bash
yarn generate
yarn account
```

3. **Nạp ETH vào tài khoản deployer** từ faucet hoặc ví của bạn

4. **Deploy lên testnet**:
```bash
yarn deploy --network sepolia
# hoặc
yarn deploy --network optimismSepolia
```

5. **Cập nhật frontend config** trong `packages/nextjs/scaffold.config.ts`:
   - Đổi `targetNetwork` thành `chains.sepolia` hoặc `chains.optimismSepolia`

6. **Deploy frontend lên Vercel**:
```bash
yarn vercel
```

### Cấu Trúc Thư Mục Quan Trọng

```
challenge-dex/
├── packages/
│   ├── hardhat/              # Smart contracts
│   │   ├── contracts/        # Solidity contracts (.sol)
│   │   ├── deploy/           # Deployment scripts
│   │   └── test/             # Test files
│   └── nextjs/               # Frontend application
│       ├── app/              # Next.js app router pages
│       ├── components/       # React components
│       └── hooks/            # Custom React hooks
└── README.md                 # File này
```

---