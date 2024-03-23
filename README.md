import requests

def create_github_repo(username, token, repo_name):
    url = f"https://api.github.com/user/repos"
    headers = {
        "Authorization": f"token {token}",
        "Accept": "application/vnd.github.v3+json"
    }
    data = {
        "name": repo_name,
        "auto_init": True  # Tạo một repository có sẵn README.md
    }

    response = requests.post(url, headers=headers, json=data)
    if response.status_code == 201:
        print(f"Repository '{repo_name}' đã được tạo thành công trên GitHub.")
        return True
    else:
        print(f"Đã xảy ra lỗi: {response.status_code} - {response.json().get('message', 'Không xác định')}")
        return False

# Thay thế các giá trị sau đây bằng thông tin GitHub của bạn
username = "huy bùi"
token = "your_personal_access_token"
repo_name = "new_repository_name"

create_github_repo(username, token, repo_name)
