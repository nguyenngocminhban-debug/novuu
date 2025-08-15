# Novu - Hướng dẫn Build và Custom

## 🚀 Quick Start

### 1. Cài đặt nhanh (Windows)

```powershell
# Chạy script tự động setup
.\setup-novu.ps1

# Hoặc setup từng bước
.\setup-novu.ps1 -SkipDocker  # Bỏ qua Docker
.\setup-novu.ps1 -SkipBuild   # Bỏ qua build
```

### 2. Cài đặt thủ công

```bash
# Clone repository
git clone https://github.com/novuhq/novu.git
cd novu

# Cài đặt dependencies
npm install -g pnpm@10.11.0
pnpm install

# Setup environment
cp ./docker/.env.example ./docker/local/development/.env

# Khởi động databases
docker-compose -f ./docker/local/development/docker-compose.yml up -d

# Build dự án
pnpm build

# Chạy dự án
pnpm start
```

## 📱 Truy cập ứng dụng

- **API**: http://localhost:3000
- **Dashboard**: http://localhost:3001
- **Web App**: http://localhost:3002

## 🎨 Custom hóa

### UI/UX

- **Dashboard**: Chỉnh sửa `apps/dashboard/src/`
- **Web App**: Chỉnh sửa `apps/web/src/`
- **Design System**: `apps/dashboard/src/design-system/`

### API

- **Controllers**: `apps/api/src/controllers/`
- **Services**: `apps/api/src/services/`
- **Modules**: `apps/api/src/modules/`

### Providers

- **Thêm provider mới**: `packages/providers/src/lib/providers/`
- **Custom logic**: Implement interface `IProvider`

### Database

- **Entities**: `apps/api/src/dal/entities/`
- **Repositories**: `apps/api/src/dal/repositories/`

## 🔧 Development Commands

```bash
# Build
pnpm build                    # Build tất cả
pnpm build:api               # Build API
pnpm build:dashboard         # Build Dashboard
pnpm build:web              # Build Web App

# Run
pnpm start                   # Chạy tất cả
pnpm start:api:dev          # Chạy API development
pnpm start:dashboard        # Chạy Dashboard
pnpm start:web              # Chạy Web App

# Code Quality
pnpm lint                   # Check code style
pnpm lint:fix              # Fix code style
pnpm format                # Format code
pnpm test                  # Run tests

# Code Generation
pnpm g:module --name=my-module
pnpm g:usecase --name=my-usecase --module=my-module
```

## 📚 Tài liệu chi tiết

- [Hướng dẫn Build và Custom](./HUONG_DAN_BUILD_CUSTOM.md)
- [Hướng dẫn Custom chi tiết](./CUSTOM_GUIDE.md)
- [Novu Documentation](https://docs.novu.co)

## 🐳 Docker

```bash
# Development
docker-compose -f docker/local/docker-compose.yml up -d

# Production
docker-compose -f docker/community/docker-compose.yml up -d

# Build images
pnpm docker:build
```

## 🔐 Environment Variables

```bash
# Database
MONGODB_URL=mongodb://localhost:27017/novu
REDIS_URL=redis://localhost:6379

# JWT
JWT_SECRET=your-jwt-secret
JWT_REFRESH_SECRET=your-refresh-secret

# Email
SENDGRID_API_KEY=your-sendgrid-key

# SMS
TWILIO_ACCOUNT_SID=your-twilio-sid
TWILIO_AUTH_TOKEN=your-twilio-token
```

## 🚨 Troubleshooting

### Lỗi thường gặp:

1. **Port conflicts**

```bash
# Kiểm tra ports
lsof -i :3000
lsof -i :3001
lsof -i :3002
```

2. **Database connection**

```bash
# Restart Docker
docker-compose down
docker-compose up -d
```

3. **Build errors**

```bash
# Clean và rebuild
pnpm clean
pnpm install
pnpm build
```

## 📋 Yêu cầu hệ thống

- **Node.js**: >= 20 < 21
- **pnpm**: ^10.0.0
- **Docker**: Để chạy databases
- **Git**: Để clone repository

## 🤝 Contributing

1. Fork repository
2. Tạo feature branch
3. Commit changes
4. Push to branch
5. Tạo Pull Request

## 📄 License

- Core: MIT License
- Enterprise: Commercial License

---

**Lưu ý**: Đây là hướng dẫn cơ bản. Xem tài liệu chi tiết để custom sâu hơn.
